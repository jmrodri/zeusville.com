---
title: 'SOAP is dirty!'
date: Fri, 14 Dec 2007 04:08:18 +0000
draft: false
tags: [Java, python, Technology, zmugfs]
categories: [Java, python, Technology, zmugfs]
type: post
---

Contrary to popular belief, [SOAP](http://en.wikipedia.org/wiki/SOAP) is dirty! When folks talk about web services they immediately think SOAP, which is unfortunate. When I think of a web service I think of system either a web site, a service running in your companies intranet, even a service running on the same machine, that I can send simple messages to and receive responses. The key is SIMPLE messages. Yes, that's a rather loose definition. Mail servers probably fall into that definition, but to me that's a web service. Well not very webby but a service nonetheless. So if SOAP is dirty what else can you use to create web services? Well there's the venerable [XML-RPC](http://en.wikipedia.org/wiki/XMLRPC) which is truly simple unlike SOAP. Most people don't use XML-RPC because it doesn't support "objects", but then again those are overrated too. Seriously folks, you send a message you get back a structure. You really don't need more than a hash or an array. Other reasons folks don't like XML-RPC are that it lacks support for long data types (only supports integers), UTF-8 encoding (makes it hard to use for internationalization), and doesn't have the concept of null. Those are all valid reasons, but a lot of times you don't need that stuff in which case it's still better to use XML-RPC rather than SOAP. The ease of development and ease of use from an api users point of view out weighs a lot of those things. XML-RPC is also trivial to understand. The specification is easy to digest: [http://www.xmlrpc.com/spec](http://www.xmlrpc.com/spec). Compare that to the monstrosity of the [SOAP spec](http://www.w3.org/TR/2000/NOTE-SOAP-20000508/). There still quite a few application that use XML-RPC as an API: [smugmug.com](http://smugmug.jot.com/XML-RPC), [func](https://hosted.fedoraproject.org/func/), [Red Hat Network](https://rhn.redhat.com/rhn/apidoc/), and [flickr](http://www.flickr.com/services/api/request.xmlrpc.html). If the limitations of XML-RPC truly are deal breakers for you, you're probably wondering "I guess I'll need to use SOAP!" Well, aside from needing soap to stay clean, you can actually be SOAP free in your web services and still use longs, nulls, etc. How? Use [REST](http://en.wikipedia.org/wiki/Representational_State_Transfer). There are two ways to implement REST services. There's the purist way which uses the verbs of the HTTP protocol such as [PUT, DELETE, POST](http://en.wikipedia.org/wiki/Representational_State_Transfer#RESTful_example:_the_World_Wide_Web), etc. The other more common way is to simply use the GET and POST. You supply your parameters on the URL including the method to be called and get back an XML response. A downside to REST is that the XML response is defined by the web service implementor, unlike XML-RPC or SOAP which have a defined structure. Nonetheless, REST has become very popular among web sites such as [smugmug.com](http://smugmug.jot.com/WikiHome/1.2.0), [amazon.com](http://docs.amazonwebservices.com/AmazonS3/2006-03-01/), and [yahoo.com](http://developer.yahoo.com/traffic/rest/V1/). REST and XML-RPC are not the only alternatives to SOAP, [JSON](http://en.wikipedia.org/wiki/JSON) is another. JSON is commonly done as a REST web service with the exception that the response is in JSON format. Most folks assume JSON is for use with JavaScript and web applications only, but that is not true. The thing I like most about JSON + REST is I get the ease of calling by a simple URL and get a well formatted easy to read response that supports nulls, UTF-8, and longs. You get none of the scum from SOAP, none of the limitations of XML-RPC, and a well understood format unlike the typical REST response. Ok the best way to "see" this is by looking at some code. Let's look at XML-RPC first. Let's assume we are calling the "smugmug.images.get" method at smugmug.com. Using an XML-RPC library for your language ([java](http://xmlrpc.sourceforge.net/), [python](http://docs.python.org/lib/module-xmlrpclib.html), [perl](http://search.cpan.org/~kmacleod/Frontier-RPC-0.07b4/lib/Frontier/Client.pm)). `client = ServerProxy("http://smugmug.com/xmlrpc") session = client.loginWithPassword("uname", "pass") imgdata = client.smugmug.images.get(session, image_id) print imgdata['id']` It's that simple. The library did the parsing for me. imgdata will most likely be a hash. The library sent over something like this:```
<?xml version="1.0"?>
  <methodCall>
    <methodName>smugmug.images.get</methodName>
      <params>
        <param>
          <value><string>AXE0123</string>
        </param>
        <param>
          <value><i4>40</i4></value>
        </param>
      </params>
   </methodCall>
```The server responds with something like this:```
<?xml version="1.0"?>
<methodResponse>
  <array>
    <data>
      <value><i4>1404</i4></value>
      <value><i4>1504</i4></value>
      <value><i4>1</i4></value>
    </data>
  </array>
</methodResponse>
```Pretty easy to read isn't it? But as you saw in the code you didn't have to know how to read it. Let's try the same thing with REST. There are no frameworks that handle REST directly as it's just a simple HTTP GET or POST and an XML document response. `url = "http://api.smugmug.com/services/api/rest/1.2.1/" call = url + "?method=smugmug.images.get&session=AXE0123&id=40" response = urllib.urlopen(call).read() # parse response XML into a dictionary imgdata = parse(response)` In most cases you'll probably have to write your own framework which isn't really that hard, [I did it](http://zmugtools.svn.sourceforge.net/viewvc/zmugtools/trunk/zmugjson/zmugjson.py?view=markup). What gets sent out is a simple HTTP GET request to http://api.smugmug.com. What you get back is an XML document which you will need to parse.```
<?xml version="1.0" encoding="utf-8" ?>
<rsp stat="ok">
 <method>smugmug.images.get</method>
 <Images>
  <Image id="17833"/>
  <Image id="17832"/>
 </Images>
</rsp>
```Yes, it's XML but so far it's not too bad is it? You're probably itching to see what JSON and SOAP can do huh? Well, heeeeere's JSON! (that's a [Johnny Carson](http://en.wikipedia.org/wiki/Johnny_carson) reference for you youngins). `url = "http://api.smugmug.com/services/api/json/1.2.1/" call = url + "?method=smugmug.images.get&session=AXE0123&id=40" response = urllib.urlopen(call).read() # use builtin python library simplejson to read imgdata = simplejson.loads(response)` The nice part about this is I don't have to parse the response because libraries like [simplejson](http://cheeseshop.python.org/pypi/simplejson) do that for me. And I can easily make the calling code generic as I did in [zmugjson.py](http://zmugtools.svn.sourceforge.net/viewvc/zmugtools/trunk/zmugjson/zmugjson.py?view=markup). Again, the request is nothing more than a simple HTTP GET. The response is a nice JSON object.```
{
  "stat":"ok",
  "method":"smugmug.images.get",
  "Images":\[
    {"id":222910058},
    {"id":222910121}
   \]
}
```As you can see it is very easy to read and no nasty XML to deal with either. Best part is you could use this in an AJAX web ui with no need to create more than one API. There you have it, nice alternatives for creating web services without using SOAP. Oh you want to see the SOAP version of the above? hrm. smugmug was wise not to create a SOAP version of the API, but here is what it would probably look like. I'm warning you, you don't want to see it. Ok here goes.```
  import org.apache.axis.client.Call;
  import org.apache.axis.client.Service;
  import javax.xml.namespace.QName;

  public class TestClient {
    public static void main(String \[\] args) {
      try {
        String endpoint =
            "http://api.smugmug.com/services/api/soap/1.2.1/";

        Service service = new Service();
        Call call = (Call) service.createCall();

        call.setTargetEndpointAddress( new java.net.URL(endpoint) );
        call.setOperationName(new QName("http://soapinterop.org/", GetImagesFromSmugmug"));

        List<Integer> ret = (List<Integer>) call.invoke( new Object\[\] { "AXE0123", new Integer(40) } );

        System.out.println("Sent 'Hello!', got '" + ret.toString() + "'");
      } catch (Exception e) {
        System.err.println(e.toString());
      }
    }
  }
```Yes, I know it's Java and not python, but that's another problem with SOAP. The better libraries are written for Java not python, perl, etc. What would the SOAP request look like you ask? Probably like this:```
<SOAP-ENV:Envelope
  xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"
  SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/"/>
   <SOAP-ENV:Body>
       <m:GetImageIds
         xmlns:m="Some-URI">
           <SessionId>AXE0123</SessionId>
           <id>40</id>
       </m:GetImageIds>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```Followed by a nasty response:```
<SOAP-ENV:Envelope
  xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"
  SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/"/>
   <SOAP-ENV:Header>
       <t:Transaction
         xmlns:t="some-URI"
         xsi:type="xsd:int" mustUnderstand="1">
           5
       </t:Transaction>
   </SOAP-ENV:Header>
   <SOAP-ENV:Body>
       <m:GetImageIds
         xmlns:m="Some-URI">
           <Images>
             <Id>1404</Id>
             <Id>1504</Id>
             <Id>1</Id>
           </Images>
       </m:GetImageIds>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```Seriously folks, it is truly possible to create web services and software as a service WITHOUT resorting to the evil that SOAP is. So the next time you plan on developing a web services api for your application consider [XML-RPC](http://en.wikipedia.org/wiki/XMLRPC), [REST](http://en.wikipedia.org/wiki/Representational_State_Transfer), and [JSON](http://en.wikipedia.org/wiki/JSON).