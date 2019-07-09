---
title: 'Hibernate continued'
date: Fri, 13 Feb 2004 10:31:05 +0000
draft: false
tags: [Java]
categories: [Java]
type: post
---

I'm trying to come up with a convincing argument for using Hibernate to replace our current proprietary persistence model.

We have two models which both use JDBC. One involves creating a helper object which exists between the domain object and a DatabaseCommand (our persistence class). The domain objects do not know how to generate SQL. They simply know that there exists a class that accepts helpers. The helper has methods like getStoreColumns() and getStoreValues() which return the columns used for inserts and their corresponding values, respectively. The helpers have direct knowledge of the domain object. The DatabaseCommand knows how to build SQL statements filling in the missing information by asking the helpers. See the UML diagram below:

 [![](http://jroller.com/resources/jmrodri/domainobjects_small.jpg)](http://jroller.com/resources/jmrodri/domainobjects.png)

Pros:
\* all SQL commands are done in one place
\* object model easier to use i.e. MyDomainClass.store() will persist the object
\* supports joins and subselects

Cons:
\* lots of helper classes are required
\* hard to understand at first since SQL is hidden
\* need to maintain SQL
\* mapping between domain objects and database done in code
\* though supported, subselects are difficult to implement

The second approach is DbCommands which effectively are classes which contain all SQL code for a given domain object, including searching, storing, loading. For example,

```
**public** **class** ExampleDbCommand {

  // ...

  **public** String dbLoadBySymbolicId(String symId)
    **throws** MyException
  {
    String str = "";

    Connection conn = null;

    // attempt to open a connection to the database
    **try** {
      conn = \_dbconn.getConnection();
    } **catch** (SQLException e) {
      // if failed then throw ScenarioException
      Logger.logError( e.toString() );
      **throw** e;
    }

    // Form SQL statement
    String sql = "Error - Sql String Not Yet Defined";
    Statement stmt = null;

    // execute SQL
    **try** {
      sql = "Select \* from NLS\_TABLE Where SYMBOLIC\_NAME = '" +
        symId + "' And LOCALE\_ID = '" +
        container.getLocale() + "'";

      Logger.log("logging.Category.Sql", sMethod + " " + sql);

      stmt = conn.createStatement();
      ResultSet rs = stmt.executeQuery(sql);

      **if** ( rs.next() ) {
        String temp = "";
        temp = rs.getString( "THE\_TEXT" );

        **if**(temp != null)
          str = temp.trim();
      }

      **if**(rs != null) {
        rs.close();
        rs = null;
      }
    } **catch** (SQLException sqle) {
      Logger.logError("dbLoadBySymbolicId " + sql + " " +
                      sqle.getMessage());
    } **finally** {
      **try** {
        **if**(stmt != null) {
          stmt.close();
          stmt = null;
        }
        **if** (conn != null)
          \_dbconn.releaseConnection();
      } **catch** (Exception ignore) {
        // do nothing
      }
    }

    **return** str;
  }

  // ...
}


```

Pros:
\* Easy to find the SQL since it will all be located in a single file
\* Since each SQL call is separate, it is easy to change the where clause of a single file
\* Easy to create complex queries such as joins, subselects, etc. Cons:
\* Not object-oriented
\* Buggy since connection code is repeated for each method meaning changes to that logic result in mutliple lines of code being changed.
\* Need to maintain SQL

So I'm trying to convince my superiors that Hibernate is a good fit. Some of the concerns will be performance, support for SQL Server, MySQL, DB2, and Oracle. Managing potentially large lists of objects. We also need the ability to do non object related SQL calls i.e. there won't be any domain objects for certain tasks.

From what I've read [Hibernate](http://www.hibernate.org) seems like a good fit, but I have to come up with a compelling argument for using Hibernate over writing our own where we have complete control. So after my long windeded explanation, I pose the questions.

**\* How are you using Hibernate?
\* How did you convince your management?
\* Have you regretted using it? If so, what would you do differently?
\* Have you had any performance related issues?
**
---
### Comments:
####
[Sebastiano Pilla](http://www.datafaber.com/blog/index.jsp "") - <time datetime="2004-02-13 04:27:56">Feb 5, 2004</time>

I'm not using Hibernate, but from what you write about your existing approach I think you could have an easier conversion to iBATIS SQL Maps (you could keep your existing SQL code mostly unchanged). You can find more about SQL Maps at: http://www.ibatis.com/common/sqlmaps.html The author is very responsive and development of new features has never stopped in the last 1.5 years (from when I started using it).
<hr />
