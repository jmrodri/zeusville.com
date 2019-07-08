---
title: 'python''s default argument values'
date: Tue, 25 Sep 2007 03:10:52 +0000
draft: false
tags: [python, zmugfs]
type: post
---

I've been trying to track down a bug for a couple days now with [zmugfs](http://zeusville.wordpress.com/2007/08/19/fuse-based-smugmug-fs/). I'm caching the tree structure returned by [smugmug.users.getTree](http://smugmug.jot.com/WikiHome/1.2.0/smugmug.users.getTree). Here's my Node class:```
class Node(object):
    def \_\_init\_\_(self, path, inode=MyStat(), children=\[\]):
        self.path = path
        self.inode = inode
        self.children = children
```To a newbie like me, this looks perfectly fine. If no inode is passed in create an instance of MyStat(), if no children are passed in create an empty list. Well guess what! That's not how python works with lists. If you do what I did above the children list is **shared**! Imagine my horror when each Node has a reference to ALL of the children of the other Nodes. EEK! A few minutes of googling and I found this page: [4.7.1 Default Argument Values](http://www.network-theory.co.uk/docs/pytut/DefaultArgumentValues.html). I changed the constructor of the Node class to be as follows:```
def \_\_init\_\_(self, path, inode=MyStat(), children=None):
    self.path = path
    self.inode = inode
    if children is None:
        self.children = \[\]
    else:
        self.children = children
```This fixed my problem.