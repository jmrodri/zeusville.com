---
title: 'Mysteriously closed connection'
date: Wed, 17 Aug 2005 15:02:23 +0000
draft: false
tags: [Java]
type: post
---

While deploying our product to our stage environment, we found a "glitch" with our Java webapp. We're using [Tomcat](http://jakarta.apache.org/tomcat/index.html) 5.0.27, [Hibernate](http://www.hibernate.org) 2.1.7c, RHEL 4 and Oracle. I'm seeing this wonderful error:

```


WARN  net.sf.hibernate.util.JDBCExceptionReporter - SQL Error: 17008, SQLState: null
ERROR net.sf.hibernate.util.JDBCExceptionReporter - Closed Connection



```Followed by:```

ERROR com.mycompany.SomeObjectFactory - HibernateException trying to commit: com.mycompany.SomeObjectImpl
net.sf.hibernate.exception.GenericJDBCException: Could not save object
...
Caused by: java.sql.SQLException: Closed Connection
        at oracle.jdbc.dbaccess.DBError.throwSqlException(DBError.java(Compiled Code))
...




```I've looked through the code and used a logging jdbc driver (which wraps the actually jdbc driver and logs statements for certain objects.) to log the Connection. No close() method was called. So from what I can gather our application isn't closing it by accident. But I can't figure out what is closing the connection.

I've already checked Oracle and it is not set to close idle connections.  
Checked the router between the DB and the application box.  
The closest I can fathom is the kernel's tcp\_keepalive\_time which is set to 7200 (which is approximately when we see the above error occur).

We'll continue our investigation, but this is indeed a perplexing problem.