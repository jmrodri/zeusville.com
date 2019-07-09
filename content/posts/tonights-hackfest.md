---
title: 'tonights hackfest'
date: Tue, 20 Mar 2007 04:07:29 +0000
draft: false
tags: [sm-photo-tool]
categories: [sm-photo-tool]
type: post
---

My work on getting sm-photo-tool to use smugmug's REST API continues. It's been slow going as I'm also learning python as I go. Tonight I can get image and album info using the REST API which returns me an XML document. I parse the document using DOM, and dynamically create a class with an internal map (or dict in python) of attributes. Here's a sample response from the getImageInfo REST API call:```
<?xml version="1.0" encoding="utf-8" ?>
<rsp stat="ok">
 <method>smugmug.images.getInfo</method>
  <Info>
   <Image id="134646762">
    <Album id="2559293" />
    <FileName>IMG\_0112.JPG</FileName>
    <Caption />
    <Keywords />
    <Position>1</Position>
    <Date>2007-03-08 17:48:25</Date>
    <Format>JPG</Format>
    <Serial>0</Serial>
    <Watermark>0</Watermark>
    <Size>2553371</Size>
    <Width>2592</Width>
    <Height>1944</Height>
    <MD5Sum>a7d81edf9fb659da1947514dbbcfb204</MD5Sum>
    <LastUpdated>2007-03-08 17:48:34</LastUpdated>
    <OriginalURL>http://familiarodriguez.smugmug.com/photos/134646762-O.jpg</OriginalURL>
    <LargeURL>http://familiarodriguez.smugmug.com/photos/134646762-L.jpg</LargeURL>
    <MediumURL>http://familiarodriguez.smugmug.com/photos/134646762-M.jpg</MediumURL>
    <SmallURL>http://familiarodriguez.smugmug.com/photos/134646762-S.jpg</SmallURL>
    <TinyURL>http://familiarodriguez.smugmug.com/photos/134646762-Ti.jpg</TinyURL>
    <ThumbURL>http://familiarodriguez.smugmug.com/photos/134646762-Th.jpg</ThumbURL>
    <AlbumURL>http://familiarodriguez.smugmug.com/gallery/2559293/1/134646762</AlbumURL>
   </Image>
  </Info>
</rsp>
```This is the class I want to create:```
class Image:
    def \_\_init\_\_(self):
        self.data = {}
    def \_\_setitem\_\_(self, key, value):
        #print "\_\_setitem\_\_(%s:%s)" % (key,value)
        self.data\[key.lower()\] = value
    def \_\_getitem\_\_(self, key):
        #print "\_\_getitem\_\_(%s)" % (key)
        return self.data\[key.lower()\]
    def \_\_str\_\_(self):
        return str(self.data)
```This makes it easy to use the resulting object.```
    print "getimageinfo ---------------------------------------"
    imgInfo = sm1.getImageInfo(sessionid, images\[0\])
    print "imageinfo: " + str(imgInfo)
    print "TinyURL = " + imgInfo\['TinyURL'\]
    print "imageid = " + imgInfo\['imageid'\]
    print "albumId = " + imgInfo\['albumId'\]
```All of the code can be found [here.](http://sm-photo-tool.svn.sourceforge.net/viewvc/sm-photo-tool/trunk/sm-photo-tool/playpen/sm_rest.py?view=markup). A more OO way is to have getter and setter methods, but I really like the ability to treat an object as a map and send it "messages". I despise getters and setters now. Off to bed now.