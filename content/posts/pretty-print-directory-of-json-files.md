---
title: 'Pretty Print directory of .json files'
date: Thu, 30 Jun 2016 18:11:58 +0000
draft: false
tags: [Linux, Personal, Technology]
categories: [Linux, Personal, Technology]
type: post
---

I had a bunch of compressed json files that I needed to pretty print to make them more readable. This little snippet will create a new pretty printed json file prefixed with pp:

`ls *.json | xargs -I {} sh -c "cat {} | python -mjson.tool > pp{}"`

Instead of having to look at files that look like this:

```
{ "attributes": \[ { "name": "type", "value": "PKT" }, { "name": "arch", "value": "x86\_64,x86" }, { "name": "name", "value": "Awesome OS" } \], "dependentProductIds": \[\], "href": "/products/00", "id": "00", "multiplier": 1, "name": "Awesome OS", "productContent": \[ { "content": { "arches": null, "contentUrl": "/content/6/$releasever/$basearch/debug", "gpgUrl": "file:///etc/pki/rpm-gpg/RPM-GPG-KEY-awesome-os", "id": "FFFF", "label": "awesome-os-debug-rpms", "metadataExpire": 86400, "modifiedProductIds": \[ "0A" \], "name": "Awesome OS (Debug RPMs)", "releaseVer": null, "requiredTags": "awesome-os-server", "type": "yum", "vendor": "Candlepin" }, "enabled": false } \] }

You get a bunch of files that look like this:

```
{

    "attributes": \[

        {

            "name": "type",

            "value": "PKT"

        },

        {

            "name": "arch",

            "value": "x86\_64,x86"

        },

        {

            "name": "name",

            "value": "Awesome OS"

        }

    \],

    "dependentProductIds": \[\],

    "href": "/products/00",

    "id": "00",

    "multiplier": 1,

    "name": "Awesome OS",

    "productContent": \[

        {

            "content": {

                "arches": null,

                "contentUrl": "/content/6/$releasever/$basearch/debug",

                "gpgUrl": "file:///etc/pki/rpm-gpg/RPM-GPG-KEY-awesome-os",

                "id": "FFFF",

                "label": "awesome-os-debug-rpms",

                "metadataExpire": 86400,

                "modifiedProductIds": \[

                    "0A"

                \],

                "name": "Awesome OS (Debug RPMs)",

                "releaseVer": null,

                "requiredTags": "awesome-os-server",

                "type": "yum",

                "vendor": "Candlepin"

            },

            "enabled": false

        }

    \]

}


```
```