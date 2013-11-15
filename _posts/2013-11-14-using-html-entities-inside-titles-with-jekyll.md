---
layout: post 
category: 
title: "Using HTML entities inside titles with Jekyll"
tagline: 
tags : [] 
published: true
---
Someone recently tried to use HTML entities inside their blog title. 

    title: <my html="tag">

Jekyll crashed when generating the page with:

    malformed XML: missing tag start

Even putting the escape character (&amp;lt;) did not work.

The solution is to do this:

    title: |
        &lt;my html="tag"&gt;


