---
layout: post 
category: 
title: "Authoring impress.js presentations from your mobile phone hosted on GitHub"
tagline: 
tags : [] 
published: false
---

If you use Jekyll to blog, did you know you can easily host impress.js presentations right inside your blog? And, did you know that if you use <a href="https://play.google.com/store/apps/details?id=com.EditorHyde.app">Teddy Hyde</a>, the Jekyll editor for Android, you can author impress.js presentations from your mobile phone, and even share them privately to solicit feedback?

First I will show you how to add impress.js presentations to your Jekyll blog via command line. Then, I will show you how to do it using your mobile phone, and hopefully you'll agree it is much easier and cooler to do it from your mobile device.

## Create impress.js in your Jekyll blog

Run these commands from the git repository of your Jekyll blog:

    curl http://blog.teddyhyde.com/impress_template.html --out _include/impress.html
    
Then, just author your Jekyll page or post using the impress layout, like so:

    ---
    layout: impress 
    title: "My first impress.js"
    published: true
    ---

The template has all the correct JavaScript libraries. Just remember to use impress.js classes to write your transitions.

Don't know the HTML for impress.js? Well, use impress.js from Teddy Hyde and you won't have to!

## Creating and authoring impress.js from your mobile phone

 

