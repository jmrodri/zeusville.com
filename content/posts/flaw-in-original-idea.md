---
title: 'flaw in original idea'
date: Fri, 31 Aug 2007 04:17:55 +0000
draft: false
tags: [zmugfs]
categories: [zmugfs]
type: post
---

There's a flaw in my thinking with [categories, subcategories, and albums](http://zeusville.wordpress.com/2007/08/24/categories-subcategories-and-albums-oh-my/). `mkdir -p /Category/Subcategory/Album` will pass in each path separately. So I don't have any context as to which is the leaf to know which one is a category vs an album. As far as call sequences, there's no difference between

`mkdir -p /Category/Subcategory/Album` and

`mkdir /Category;`

`mkdir /Category/Subcategory/;`

`mkdir /Category/Subcategory/Album.` My plan was to make leaf directories as albums, the paths above would be categories. After each call I don't know if there is more until the next call. The user wants Subcategory to be a category, but I would end up creating an Album, until the next call which it shows that Subcategory was a category, but then what is Album? Is there going to be another call after that?

Another option is to take an approache similar to [flickrfs](http://manishrjain.googlepages.com/flickrfs) which uses a preconfigured [structure](http://manishrjain.googlepages.com/flickrfs#structure):

`/sets`

`/tags/personal`

`/tags/public`

`/stream`

But I'm unsure how usable that would be for smugmug.

`/categories (subcategories are implied)`

`/albums`

I could create both a category and an album for each level. So how will work, if you call mkdir -p /Family/Party/Susie you will end up with the following categories: Family, Party, and Susie. You will also have the same set of albums. hrm, this is less than optimal as well.

Another approach is for each mkdir call I create a (sub)category. The minute you copy a photo into a directory, it becomes an Album. Now should I remove the category? I guess I should if there are no images for that category. Let's walk through an example:

`mkdir -p /Family/Children/Birthday/Susie`

This results in the mkdir method being called with the following paths: /Family, /Family/Children, /Family/Children/Birthday, /Family/Children/Birthday/Susie. This will result in the following (sub)categories being created: Family, Children, Birthday, Susie. Is this what the user wants? Or did they truly want an empty Susie album? Let's keep going. When the user does a `cp IMG_2020.JPG /Family/Children/Birthday/Susie` I know here that Susie is an album. I can now create the Album, then upload the picture to that Album. The problem here is if the Album creation fails, what do I do? They thought it was already created. I guess this isn't such a horrible option. For now lets go with this approach. We'll create a (sub)category for each level in the path, until a copy to the directory occurs. At that point the category gets "promoted" to an Album. If the (sub)category contains no images, we remove it. /me crosses fingers.