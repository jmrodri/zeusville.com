---
title: 'Re-run a modified ActiveRecord Migration'
date: Wed, 18 Feb 2015 21:51:18 +0000
draft: false
tags: [activerecord, migrations, rails, ruby]
categories: [Linux, Ruby]
type: post
---

Rails has this cool feature called ActiveRecord Migration. It's an easy way to create and update your database. But if you get it wrong it is super annoying. This is where migrations and me loathe each other. I had a migration which had the wrong column names. Now I could easily create another migration to change the names, but I'm still developing and I don't want yet another migration. First thing I did was modified the migration before rolling things back. That is definitely going to fail. SO I reverted my changes.```
class AddRhevParams < ActiveRecord::Migration
  def change
    remove\_column :fusor\_deployments, :rhev\_params
    add\_column :fusor\_deployments, :rhev\_hypervisor\_host\_id, :integer
    add\_column :fusor\_deployments, :rhev\_engine\_host\_id, :integer
    add\_column :fusor\_deployments, :rhev\_hypervisor, :string
    add\_column :fusor\_deployments, :rhev\_engine, :string
    add\_column :fusor\_deployments, :rhev\_database, :string
    add\_column :fusor\_deployments, :rhev\_cluster, :string
    add\_column :fusor\_deployments, :rhev\_storage, :string
    add\_column :fusor\_deployments, :rhev\_cpu, :string
    add\_column :fusor\_deployments, :rhev\_share, :string
  end
end

```First I tried `rake db:rollback STEP=1` hoping that it would put the DB in the state prior to my latest migration. For whatever reason it failed with an IrreversableMigration error.```
$ rake db:rollback STEP=1
The Apipie cache is turned off. Enable it and run apipie:cache rake task to speed up API calls.
Workaround for RbVmomi may not work as ComputeResource is already loaded: ComputeResource
\[deprecated\] I18n.enforce\_available\_locales will default to true in the future. If you really want to skip validation of your locale you can set I18n.enforce\_available\_locales = fal
se to avoid this message.
==  AddRhevParams: reverting ==================================================
rake aborted!
StandardError: An error has occurred, this and all later migrations canceled:

ActiveRecord::IrreversibleMigration/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration/command\_recorder.rb:42:in \`block in inverse'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration/command\_recorder.rb:40:in \`map'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration/command\_recorder.rb:40:in \`inverse'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration.rb:401:in \`block (3 levels) in migrate'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration.rb:358:in \`revert'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration.rb:400:in \`block (2 levels) in migrate'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration.rb:399:in \`block in migrate'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/connection\_adapters/abstract/connection\_pool.rb:129:in \`with\_connection'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration.rb:389:in \`migrate'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration.rb:528:in \`migrate'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration.rb:720:in \`block (2 levels) in migrate'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration.rb:775:in \`call'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration.rb:775:in \`block in ddl\_transaction'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/connection\_adapters/abstract/database\_statements.rb:192:in \`transaction'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/transactions.rb:208:in \`transaction'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration.rb:775:in \`ddl\_transaction'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration.rb:719:in \`block in migrate'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration.rb:700:in \`each'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration.rb:700:in \`migrate'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration.rb:574:in \`down'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration.rb:656:in \`move'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration.rb:562:in \`rollback'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/railties/databases.rake:276:in \`block (2 levels) in '
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/bin/ruby\_executable\_hooks:15:in \`eval'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/bin/ruby\_executable\_hooks:15:in \`'
caused by: (ActiveRecord::IrreversibleMigration) ActiveRecord::IrreversibleMigration
    ... skipped 46 lines
ActiveRecord::IrreversibleMigration: ActiveRecord::IrreversibleMigration
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration/command\_recorder.rb:42:in \`block in inverse'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration/command\_recorder.rb:40:in \`map'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration/command\_recorder.rb:40:in \`inverse'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration.rb:401:in \`block (3 levels) in migrate'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration.rb:358:in \`revert'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration.rb:400:in \`block (2 levels) in migrate'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration.rb:399:in \`block in migrate'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/connection\_adapters/abstract/connection\_pool.rb:129:in \`with\_connection'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration.rb:389:in \`migrate'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration.rb:528:in \`migrate'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration.rb:720:in \`block (2 levels) in migrate'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration.rb:775:in \`call'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration.rb:775:in \`block in ddl\_transaction'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/connection\_adapters/abstract/database\_statements.rb:192:in \`transaction'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/transactions.rb:208:in \`transaction'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration.rb:775:in \`ddl\_transaction'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration.rb:719:in \`block in migrate'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration.rb:700:in \`each'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration.rb:700:in \`migrate'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration.rb:574:in \`down'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration.rb:656:in \`move'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration.rb:562:in \`rollback'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/railties/databases.rake:276:in \`block (2 levels) in '
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/bin/ruby\_executable\_hooks:15:in \`eval'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/bin/ruby\_executable\_hooks:15:in \`'
Tasks: TOP => db:rollback
(See full trace by running task with --trace)

```Then I tried `rake db:migrate:down --trace VERSION=` and that failed with the same error.```
$ rake db:migrate:down --trace VERSION=20150216190947
\*\* Invoke db:migrate:down (first\_time)
\*\* Invoke environment (first\_time)
\*\* Execute environment
The Apipie cache is turned off. Enable it and run apipie:cache rake task to speed up API calls.
Workaround for RbVmomi may not work as ComputeResource is already loaded: ComputeResource
\[deprecated\] I18n.enforce\_available\_locales will default to true in the future. If you really want to skip validation of your locale you can set I18n.enforce\_available\_locales = fal
se to avoid this message.
\*\* Invoke db:load\_config (first\_time)
\*\* Execute db:load\_config
\*\* Execute db:migrate:down
==  AddRhevParams: reverting ==================================================
rake aborted!
ActiveRecord::IrreversibleMigration: ActiveRecord::IrreversibleMigration
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration/command\_recorder.rb:42:in \`block in inverse'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration/command\_recorder.rb:40:in \`map'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration/command\_recorder.rb:40:in \`inverse'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration.rb:401:in \`block (3 levels) in migrate'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration.rb:358:in \`revert'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration.rb:400:in \`block (2 levels) in migrate'
/home/vagrant/.rvm/rubies/ruby-1.9.3-p448/lib/ruby/1.9.1/benchmark.rb:280:in \`measure'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration.rb:399:in \`block in migrate'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/connection\_adapters/abstract/connection\_pool.rb:129:in \`with\_connection'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration.rb:389:in \`migrate'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration.rb:528:in \`migrate'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration.rb:679:in \`run'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/migration.rb:578:in \`run'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/gems/activerecord-3.2.21/lib/active\_record/railties/databases.rake:238:in \`block (3 levels) in '
/home/vagrant/.rvm/gems/ruby-1.9.3-p448@global/gems/rake-10.4.2/lib/rake/task.rb:240:in \`call'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448@global/gems/rake-10.4.2/lib/rake/task.rb:240:in \`block in execute'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448@global/gems/rake-10.4.2/lib/rake/task.rb:235:in \`each'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448@global/gems/rake-10.4.2/lib/rake/task.rb:235:in \`execute'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448@global/gems/rake-10.4.2/lib/rake/task.rb:179:in \`block in invoke\_with\_call\_chain'
/home/vagrant/.rvm/rubies/ruby-1.9.3-p448/lib/ruby/1.9.1/monitor.rb:211:in \`mon\_synchronize'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448@global/gems/rake-10.4.2/lib/rake/task.rb:172:in \`invoke\_with\_call\_chain'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448@global/gems/rake-10.4.2/lib/rake/task.rb:165:in \`invoke'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448@global/gems/rake-10.4.2/lib/rake/application.rb:150:in \`invoke\_task'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448@global/gems/rake-10.4.2/lib/rake/application.rb:106:in \`block (2 levels) in top\_level'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448@global/gems/rake-10.4.2/lib/rake/application.rb:106:in \`each'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448@global/gems/rake-10.4.2/lib/rake/application.rb:106:in \`block in top\_level'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448@global/gems/rake-10.4.2/lib/rake/application.rb:115:in \`run\_with\_threads'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448@global/gems/rake-10.4.2/lib/rake/application.rb:100:in \`top\_level'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448@global/gems/rake-10.4.2/lib/rake/application.rb:78:in \`block in run'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448@global/gems/rake-10.4.2/lib/rake/application.rb:176:in \`standard\_exception\_handling'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448@global/gems/rake-10.4.2/lib/rake/application.rb:75:in \`run'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448@global/gems/rake-10.4.2/bin/rake:33:in \`'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448@global/bin/rake:19:in \`load'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448@global/bin/rake:19:in \`'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/bin/ruby\_executable\_hooks:15:in \`eval'
/home/vagrant/.rvm/gems/ruby-1.9.3-p448/bin/ruby\_executable\_hooks:15:in \`'
Tasks: TOP => db:migrate:down

```Doing some googling, I found you can run `rails console` and run the migrations by hand, see [Executing Migration Commands From Rails Console](http://pmatsinopoulos.github.io/blog/2012/09/25/executing-migration-commands-from-rails-console/). I then ran these commands in my rails console:```
ActiveRecord::Migration.remove\_column :fusor\_deployments, :rhev\_hypervisor\_host\_id
ActiveRecord::Migration.remove\_column :fusor\_deployments, :rhev\_engine\_host\_id
ActiveRecord::Migration.remove\_column :fusor\_deployments, :rhev\_hypervisor
ActiveRecord::Migration.remove\_column :fusor\_deployments, :rhev\_engine
ActiveRecord::Migration.remove\_column :fusor\_deployments, :rhev\_database
ActiveRecord::Migration.remove\_column :fusor\_deployments, :rhev\_cluster
ActiveRecord::Migration.remove\_column :fusor\_deployments, :rhev\_storage
ActiveRecord::Migration.remove\_column :fusor\_deployments, :rhev\_cpu
ActiveRecord::Migration.remove\_column :fusor\_deployments, :rhev\_share
ActiveRecord::Migration.add\_column :fusor\_deployments, :rhev\_params, :text

```Then I went into the database and deleted the reference to my migration from the `schema_migrations`.```
\=# delete from schema\_migrations where version = '20150216190947';

```That cleaned up the migration and I was able to rerun using `rake db:migrate````
class AddRhevParams < ActiveRecord::Migration
  def change
    remove\_column :fusor\_deployments, :rhev\_params
    add\_column :fusor\_deployments, :rhev\_hypervisor\_host\_id, :integer
    add\_column :fusor\_deployments, :rhev\_engine\_host\_id, :integer
    add\_column :fusor\_deployments, :rhev\_hypervisor\_hostname, :string
    add\_column :fusor\_deployments, :rhev\_engine\_hostname, :string
    add\_column :fusor\_deployments, :rhev\_database\_name, :string
    add\_column :fusor\_deployments, :rhev\_cluster\_name, :string
    add\_column :fusor\_deployments, :rhev\_storage\_name, :string
    add\_column :fusor\_deployments, :rhev\_storage\_type, :string
    add\_column :fusor\_deployments, :rhev\_storage\_address, :string
    add\_column :fusor\_deployments, :rhev\_cpu\_type, :string
    add\_column :fusor\_deployments, :rhev\_share\_path, :string
  end
end

```So if you have trouble rolling things back automatically, you can try using `rails console` and mucking with the `schema_migrations` database table.