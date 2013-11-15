---
layout: post 
category: 
title: "Using HTML entities inside titles with Jekyll"
tagline: 
tags : [] 
published: false
---
Someone recently tried to use HTML entities inside their blog title. Jekyll crashed when generating the page with:

    malformed XML: missing tag start

Even putting the escape character (\&lt;) did not work.

The solution is to do this:

    title: |
        &lt;%my html="tag"%&gt;


