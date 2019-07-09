---
title: 'Hibernate not suited for normalized databases'
date: Sat, 22 May 2004 22:11:57 +0000
draft: false
tags: [Java]
categories: [Java]
type: post
---

On my current project our database is highly normalized to support high volumes of data. We decided to investigate persistence frameworks with a bias towards [Hibernate](http://www.hibernate.org) which has a reputation for being the best persistence framework at current. While it is well suited for a situation where you have one object per table (seems like a typical paradigm for web applications), it is not suited for heavily normalized tables.

In the past, I've posted about recommending Hibernate (see my [JavaLobby](http://www.javalobby.org) [article](http://www.javalobby.org/thread.jspa?forumID=61&threadID=11370&start=0&mode=flat)), but couldn't find a proper use of it in our application. We have several tables sometimes upto three for a given object. Hibernate doesn't seem to do this. Many have said "Hibernate can handle multiple tables per object" but few have actually explained how to do it. Many have also said, "Why don't you make use one object per table" because we can't change our database tables.

We're going to roll our own mapping and hope for the best. In the process, I will checkout [iBATIS](http://www.ibatis.com) as well as [OBJ](http://db.apache.org/ojb/).

_Other Hibernate entries_

[Angsuman's Blog](http://blog.taragana.com/index.php?p=41)  

If you have examples of an object being loaded from multiple tables and the ability to use hand tuned SQL queries (without the use of [HQL](http://www.hibernate.org/hib_docs/reference/en/html/queryhql.html)) feel free to comment.
---
### Comments:
#### 
[max]( "max@hibernate.org") - <time datetime="2004-05-23 05:03:37">May 0, 2004</time>

just a couple of things.... 1. hibernate does support which allows you to join tables together to form a new object. (in hibernate3 you will get even more - its in the v22branch now) 2. createSQLQuery() is available now to hand-tune your needs. Also in v22branch you will find support for customsql in the the persisters for create, update and delete.
<hr />
#### 
[Carlos E. Perez](http://www.manageability.org "ceperez@yahoo.com") - <time datetime="2004-05-23 06:41:00">May 0, 2004</time>

"... is highly normalized to support high volumes of data" Shouldn't the above statement read "highly de-normalized"? Normalization can lead to lower performance not the other way around. The reason you normalize is so that you get better data integrity, not because you want to support "high volumes of data".
<hr />
#### 
[Christian]( "christian@hibernate.org") - <time datetime="2004-05-23 07:32:04">May 0, 2004</time>

Normalization is the process of removing redundancy in your data structure. It has nothing to do with performance. Just because your DMBS sucks if it has to do more than 5 nested loop joins doesn't make normalization bad or even unneccessary. "Denormalization" is a term often used by snake oil salesmen right before they sell you some "data warehousing". Hibernate2 supports "multiple objects per table" (it should really be a class to table mapping, because object is a nonsense term) quite easily: You can map an entity persistent class and many dependent persistent classes to a single table. This is a good thing and it has nothing to do with normalization. In fact, the Hibernate3 will allow you to map broken, legacy, non-normalized data structures. It's really amazing what the Java "community" (or better, individual bloggers) know and don't know about data management.
<hr />
#### 
[Christian Bauer]( "christian@hibernate.org") - <time datetime="2004-05-23 07:44:12">May 0, 2004</time>

This blog eats code snippets and line breaks in comments, so I doubt anyone can actually post any examples.
<hr />
#### 
[]( "") - <time datetime="2004-05-23 12:03:01">May 0, 2004</time>

Why not create denormalized views of your data, and map hibernate classes to these views? Anything is better than rolling your own.
<hr />
#### 
[Garth Dahlstrom]( "ironstorm@users.sf.net") - <time datetime="2004-05-23 22:17:27">May 0, 2004</time>

##### "Denormalization" is a term often used by snake oil salesmen right before they sell you some "data warehousing".

While in the trivial app there is no execuse not to normalize your data completely... In the general case, the extent to which one should normalize or denormalize a database depends on the complexity of the data relationships (i.e. # of JOINs) and the performance required to meet the application's volumes.

Perhaps Hibernate changes that by storing relationships differently...
<hr />
#### 
[Gavin]( "") - <time datetime="2004-05-23 23:09:23">May 0, 2004</time>

I gotta say, I found this blog entry incredibly confusing. I'm not at all sure what you are trying to get at. Certainly Hibernate tends to assume a highly -normalized- relational model. Are you talking about /de/normalized data models, as the other commentors have assumed? Or is your problem that you have a highly "denormalized" /object model/, that you try to map to a normalized data base. In that case, you should fix your object model. We believe in very fine-grained object models, where there are "more classes than tables". This is simply more object-oriented. If you have more tables than objects, most likely your object model sucks.
<hr />
#### 
[Chip Turner]( "cturner@pattern.net") - <time datetime="2004-05-24 11:42:52">May 1, 2004</time>

To clarify some of Jesus' points (we are coworkers).  
  
The database in question is a highly normalized database, with the vast majority of the data in fourth normal form. It is a legacy database and one we can't change easily (though in most cases we wouldn't want to because of the highly tuned nature of the schema).  
  
The problem we had with Hibernate was that Hibernate, although clearly supporting normalization to a certain degree, seems to force a limit on that, as well as mandating certain object structure based on the table structure.  
  
Some examples.  
  
Suppose you have a User table. Suppose you also have a UserPersonalInfo table that stores personal info (full name, etc) about a user. Suppose this is a one-to-at-most-one relationship (ie, for every User, there may be at most one UserPersonalInfo). The object model we wanted in a case like this would be opaque to application code as to whether a UPI record existed at all, and opaque as to whether a given field came from either table. In other words, if a column migrated from UPI to U, we wouldn't have to change code. Hibernate would let you make a getUserPersonalInfo method on your User object, but there was no way we found to make it create a single object with methods for all the columns. And please don't suggest using a view -- that clearly is a workaround to a deficiency in the tool. Hibernate should abstract away the database's structure, not count on features of the database itself to.  
  
Also, suppose you have a grouping structure on your Users. Each group can have associated with it a label indicating it is a special group (like 'Admin'). So you have a User, a UserGroup, a UserGroupMembers (mapping user\_id's to user\_group\_id's). You also have a UserGroupType table with the special flags. A UserGroup may have a type or it may have a NULL type.  
  
What would be nice is to have a method on your User object called setRole or checkRole that, when passed a role type (such as 'Admin') would Do The Right Thing. Instead, you are forced to do something like getGroups to get a list of groups, then iterate those groups, then call each group's getGroupType and compare to 'Admin'. Hibernate turns each table more or less into an object, sure, but if you're having to create fifty objects and iterate in O(n) over those lists, performance is going to such. Better would be able to teach Hibernate to use a Hash inside the User object to track which of the UserGroupTypes the User has associated with them, and how to make changes when a change is requested.  
  
We had a number of examples like that; hopefully I've represented those clearly enough to explain the difficulties we encountered.  
  
It is important to say I don't know really of **any** tool on the market that really would have been sufficient here. This is a large, complicated application that is not some simple application. In the end, we decided to write maybe 1500-2500 lines of code to handle our needs instead of writing 250 to try to force a 30,000 line project that pulls in dozens of extra external dependencies into a mold it didn't seem to really fit.  
  
One thing I hope readers will resist the temptation of the easy answers of 'change your schema' or 'use views.' Both of those are copouts to real problems and are so frequently the first line of defense against genuine critique that it makes me think that people react with those kneejerk responses without actually considering the problem at hand or trying to see if perhaps there is a weakness in the product (or just saying the product doesn't do it and accepting it as a conscious decision to not offer a solution to a given type of problem). I'm not saying the responses so far have done that, but I'd much rather see this be a discussion to gain genuine understanding of the problem at hand than a flamewar.  
  
Chip
<hr />
#### 
[Rob Jellinghaus]( "robj at nimblefish dot com") - <time datetime="2004-05-24 13:32:21">May 1, 2004</time>

I think there is a lot more you could do with Hibernate than you seem to realize. To use your User-to-UserPersonalInfo example: you could have the User mapped to automatically fetch its associated UserPersonalInfo on load. Then you could make the UserPersonalInfo field of User private, and you could implement your own accessors on User that just delegate to UserPersonalInfo. Presto: your User class presents all the data available in both User and UserPersonalInfo, and you have the freedom to move columns around without changing the external interface of User. Likewise, you could just implement the whole UserGroup business as a simple bidirectional one-to-many association from User to UserGroup (via the UserGroupMembers association table). UserGroups would automatically load their UserGroupType (as configured in their mapping). Then you implement your own method on User to provide the simple API for establishing role membership. Basically I don't see where you couldn't add your own methods to the basic Hibernate classes to do everything you want to do, quite straightforwardly. It may well be that you didn't get deep enough into Hibernate to get a real feel for how the tool is used. If, for instance, you thought that you needed a UserGroupMembers class, then you definitely didn't understand how associations are implemented in Hibernate (association tables are not exposed in the object model). Cheers! Rob
<hr />
#### 
[Rob Jellinghaus]( "robj at nimblefish dot com") - <time datetime="2004-05-24 13:33:28">May 1, 2004</time>

Aargh, sorry, didn't use HTML tags in that last post. (I'm used to Wikis and web forums.) Apologies for the seemingly run-on paragraph.

Cheers,

Rob
<hr />
#### 
[Chip Turner]( "cturner@pattern.net") - <time datetime="2004-05-24 13:56:57">May 1, 2004</time>

We realized we could have done all of those things. But at that point all Hibernate is really buying is a convenient way to map columns of simple beans to tables, and it is up to the application itself to maintain those relationships. That's not much fun and we still end up doing a lot of work for each table to bend around how Hibernate thinks things should be done.  
  
Specifically, we knew we didn't need a UserGroupMembers class. But we **would** need to represent the membership manually, or by instantiating entire group objects and holding them in memory to ask simple role questions. I can write SQL to load the roles and keep only the strings (or objects) much more easily than having to bend and warp around the structure Hibernate offers for handling this kind of relationship.  
  
In the end, Hibernate just ended up being a simple bean persister for most of our examples, and that wasn't enough justification to use such a large framework. If we have to write all sorts of logic to dance around the object structure a given OR mapping tool provides, what have we really gained? The net result is we'll be using some home-grown classes to handle simple bean persistence (even cross-table persistence). It means a slight amount of more upfront work but it also means we don't have to develop internal expertise in large frameworks that we don't use most of. Slightly more code we write now in exchange for an order of magnitude less code we have to understand is a clear gain.  
  
For our project, that was the right decision, and seems to us to be something generally true of OR mapping tools vs highly normalized schemas. But there are plenty of uses for such tools and nothing wrong with using them when they make sense.  
  
Chip
<hr />
#### 
[Carlos E. Perez](http://www.manageability.org "ceperez@yahoo.com") - <time datetime="2004-05-26 07:00:12">May 3, 2004</time>

What's wrong with the logic here and why do I hear this kind of logic all too often? It's like tool A doesn't seem to work the way I think it should work for my special situation. Therefore, its inadequate and I should roll up my own implementation. It's called Not Invented Here syndrom (NIH) this is the logic that leads to the conclusion. The true motivations may lie somewhere else but it's usually the logic above that justifies it. Granted that you only use a subset of Hibernate for your "simple bean persistence" would it not be a choice that relieves you from having to do extensive testing on your own framework? The tradeoff is learning a subset of a framework versus writing your own and testing it. It's an obvious choice to make, unfortunately like just about everyone else, we've got unique needs, so let's write it again!
<hr />
#### 
[Ryan Bloom]( "rbb@redhat.com") - <time datetime="2004-05-26 08:57:57">May 3, 2004</time>

To start off, I work with Chip and Jesus.

Second, this isn't NIH syndrome. NIH would be if hibernate did what we needed it to do, and we still refused to use it. In this case, hibernate doesn't fulfill our core requirement of having one object split among many tables. The little bit of hibernate that we could use doesn't justify actually using hibernate. There are valid reasons not to bring in a large tool when you will only be using a small subset of the tool.

1) We have to do a license verification on the whole tool and all of its dependancies. In this case, that is a large undertaking, because hibernate pulls in a lot of other packages.

2) It bloats our product with a large amount of code that we just aren't going to use. The more code there is, the more stuff needs to be security audited.

The solution to this, is to create tools using the standard Unix mindset. A bunch of very small tools working together to solve a bigger problem. If that is done, then people can use just the parts they need and not have the problems associated with integrating large projects. Unfortunately, this mindset isn't one that I see a lot of open source java projects taking. More and more often, I see java projects that try to solve all problems in one big package.

Ryan
<hr />
#### 
[Kevin Dangoor](http://wwww.blueskyonmars.com "") - <time datetime="2004-05-26 12:20:39">May 3, 2004</time>

It will be interesting to hear in a year how much ocde you're maintaining in your "home-grown classes to handle simple bean persistence". The plus, certainly, is that it does precisely what you want in a way that fits your mental model. On the flip side, that's additional code inventory for you to manage. By the way, Hibernate can easily manage a Set of strings for your roles (not everything has to be a user-defined class). It is entirely possible that OR mappers would be difficult to use with your schema (no one outside of your organization could say for sure without seeing the schema). We're lucky on our project in that our database design was driven by our objects instead of the other way around. Hibernate is easy to use in that scenario. Kevin
<hr />
#### 
[Ryan Bloom]( "rbb@redhat.com") - <time datetime="2004-05-26 13:51:52">May 3, 2004</time>

To start off, I work with Chip and Jesus.

Second, this isn't NIH syndrome. NIH would be if hibernate did what we needed it to do, and we still refused to use it. In this case, hibernate doesn't fulfill our core requirement of having one object split among many tables. The little bit of hibernate that we could use doesn't justify actually using hibernate. There are valid reasons not to bring in a large tool when you will only be using a small subset of the tool.

1) We have to do a license verification on the whole tool and all of its dependancies. In this case, that is a large undertaking, because hibernate pulls in a lot of other packages.

2) It bloats our product with a large amount of code that we just aren't going to use. The more code there is, the more stuff needs to be security audited.

The solution to this, is to create tools using the standard Unix mindset. A bunch of very small tools working together to solve a bigger problem. If that is done, then people can use just the parts they need and not have the problems associated with integrating large projects. Unfortunately, this mindset isn't one that I see a lot of open source java projects taking. More and more often, I see java projects that try to solve all problems in one big package.

Ryan
<hr />
#### 
[Jesus M. Rodriguez](http://www.jroller.com/page/jmrodri "jmrodri@nc.rr.com") - <time datetime="2004-05-26 14:05:21">May 3, 2004</time>

I agree with Kevin Dangoor that hibernate would be easy to use if the database was driven the objects. But there are several systems out there that are data driven (i.e. legacy tables, etc.)

And when I started this entry, I was hoping that Hibernate users would chime in with concrete examples.

Contrary to Christian Bauers post this blog handles HTML formatting just fine. So using <pre> works ok for your code snippets.

```
public class Foo {
    // test
}

```
<hr />
#### 
[Ryan Bloom]( "rbb@redhat.com") - <time datetime="2004-05-26 16:12:18">May 3, 2004</time>

To start off, I work with Chip and Jesus.

Second, this isn't NIH syndrome. NIH would be if hibernate did what we needed it to do, and we still refused to use it. In this case, hibernate doesn't fulfill our core requirement of having one object split among many tables. The little bit of hibernate that we could use doesn't justify actually using hibernate. There are valid reasons not to bring in a large tool when you will only be using a small subset of the tool.

1) We have to do a license verification on the whole tool and all of its dependancies. In this case, that is a large undertaking, because hibernate pulls in a lot of other packages.

2) It bloats our product with a large amount of code that we just aren't going to use. The more code there is, the more stuff needs to be security audited.

The solution to this, is to create tools using the standard Unix mindset. A bunch of very small tools working together to solve a bigger problem. If that is done, then people can use just the parts they need and not have the problems associated with integrating large projects. Unfortunately, this mindset isn't one that I see a lot of open source java projects taking. More and more often, I see java projects that try to solve all problems in one big package.

Ryan
<hr />
#### 
[Ryan Bloom]( "rbb@redhat.com") - <time datetime="2004-05-26 16:13:29">May 3, 2004</time>

Didn't mean to repost just now, I accidentally answered yes to Re-Post the post data when I refreshed. Sorry

Ryan
<hr />
