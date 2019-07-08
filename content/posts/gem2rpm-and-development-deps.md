---
title: 'gem2rpm and development deps'
date: Fri, 05 Nov 2010 13:35:46 +0000
draft: false
tags: [Linux, Technology]
type: post
---

[gem2rpm](http://www.fooplanet.com/projects/gem2rpm/) seems to have an issue with 'development\_dependencies'. Some gems have both dependencies and development\_dependencies and gem2rpm treats both of these as 'Requires:' in the rpm spec. This can lead to packaging rpms you don't need. See this [stackoverflow post](http://stackoverflow.com/questions/2446817/gem2rpm-includes-all-dependencies-instead-of-including-only-runtime-dependencies) I took the patch from that post and created a new template:```
\# Generated from <%= File::basename(format.gem\_path) %> by gem2rpm -\*- rpm-spec -\*-
%define ruby\_sitelib %(ruby -rrbconfig -e "puts Config::CONFIG\['sitelibdir'\]")
%define gemdir %(ruby -rubygems -e 'puts Gem::dir' 2>/dev/null)
%define gemname <%= spec.name %>
%define geminstdir %{gemdir}/gems/%{gemname}-%{version}

Summary: <%= spec.summary.gsub(/\\.$/, "") %>
Name: rubygem-%{gemname}
Version: <%= spec.version %>
Release: 1%{?dist}
Group: Development/Languages
License: GPLv2+ or Ruby
URL: <%= spec.homepage %>
Source0: <%= download\_path %>%{gemname}-%{version}.gem
BuildRoot: %{\_tmppath}/%{name}-%{version}-%{release}-root-%(%{\_\_id\_u} -n)
Requires: rubygems
<% for d in spec.dependencies %>
<% if d.type == :runtime %>
<% for req in d.version\_requirements.to\_rpm %>
Requires: rubygem(<%= d.name %>) <%= req  %>
<% end %>
<% end %>
<% end %>
BuildRequires: rubygems
<% if spec.extensions.empty? %>
BuildArch: noarch
<% end %>
Provides: rubygem(%{gemname}) = %{version}

%description
<%= spec.description.to\_s.chomp.word\_wrap(78) + "\\n" %>

<% if nongem %>
%package -n ruby-%{gemname}
Summary: <%= spec.summary.gsub(/\\.$/, "") %>
Group: Development/Languages
Requires: rubygem(%{gemname}) = %{version}
<% spec.files.select{ |f| spec.require\_paths.include?(File::dirname(f)) }.reject { |f| f =~ /\\.rb$/ }.collect { |f| File::basename(f) }.each do |p| %>
Provides: ruby(<%= p %>) = %{version}
<% end %>
%description -n ruby-%{gemname}
<%= spec.description.to\_s.chomp.word\_wrap(78) + "\\n" %>
<% end # if nongem %>

%prep

%build

%install
rm -rf %{buildroot}
mkdir -p %{buildroot}%{gemdir}
<% rdoc\_opt = spec.has\_rdoc ? "--rdoc " : "" %>
gem install --local --install-dir %{buildroot}%{gemdir} \\
            --force <%= rdoc\_opt %>%{SOURCE0}
<% unless spec.executables.empty? %>
mkdir -p %{buildroot}/%{\_bindir}
mv %{buildroot}%{gemdir}/bin/\* %{buildroot}/%{\_bindir}
rmdir %{buildroot}%{gemdir}/bin
find %{buildroot}%{geminstdir}/bin -type f | xargs chmod a+x
<% end %>
<% if nongem %>
mkdir -p %{buildroot}%{ruby\_sitelib}
<% spec.files.select{ |f| spec.require\_paths.include?(File::dirname(f)) }.each do |p| %>
ln -s %{gemdir}/gems/%{gemname}-%{version}/<%= p %> %{buildroot}%{ruby\_sitelib}
<% end %>
<% end # if nongem %>

%clean
rm -rf %{buildroot}

%files
%defattr(-, root, root, -)
<% for f in spec.executables %>
%{\_bindir}/<%= f %>
<% end %>
%{gemdir}/gems/%{gemname}-%{version}/
<% if spec.has\_rdoc %>
%doc %{gemdir}/doc/%{gemname}-%{version}
<% end %>
<% for f in spec.extra\_rdoc\_files %>
%doc %{geminstdir}/<%= f %>
<% end %>
%{gemdir}/cache/%{gemname}-%{version}.gem
%{gemdir}/specifications/%{gemname}-%{version}.gemspec

<% if nongem %>
%files -n ruby-%{gemname}
%defattr(-, root, root, -)
%{ruby\_sitelib}/\*
<% end # if nongem %>

%changelog
\* <%= Time.now.strftime("%a %b %d %Y") %> <%= packager %> - <%= spec.version %>-1
- Initial package

```I then created an alias for gem2rpm:```
alias gem2rpm='/usr/bin/gem2rpm -t $HOME/gem2rpm.template'
```This bug caused me to almost package 20 gems for [buildr](http://buildr.apache.org). Using the above template I was able to reduce that to 5 since the rest were already in [Fedora](http://fedoraproject.org/get-fedora).