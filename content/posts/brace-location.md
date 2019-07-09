---
title: 'Brace location'
date: Thu, 02 Oct 2003 15:05:05 +0000
draft: false
tags: [Java]
categories: [Java]
type: post
---

When I was developing in C++ I was always an advocate of placing the brace at the end of the line instead of on a new line.  
```
NewsLetter::NewsLetter( istream& str ) {
    while( str ) {
...

```

Then I made the switch to Java and decided that the brace should be placed on a new line.  

```
public class Foo
{
...

```

This was because I thought it was easier to read. But it turns out it was because I was writing methods that were way too long and cumbersome to understand. Now I'm writing smaller methods which work well with the brace at the end of the first line. Another style I saw which I do think is bizarre is placing the brace on a new line, then placing code directly after it.

```
public class Foo
{ Foo()
  { System.out.println( "Hello World" );
  }
}

```

But I believe that the best way to go is let the developer choose their format of choice. If a consistent look is required then use an automated tool to cleanup the code during build time.
---
### Comments:
#### 
[Jan Kruger]( "tiaank@mandleve.com") - <time datetime="2003-10-02 14:21:34">Oct 4, 2003</time>

I am in support of the first option, as putting the { on the first line saves overall whitespace, which can sometimes make a file with many small methods very overwhelming.
<hr />
