---
layout: post 
category: 
title: "We don't write to your profile. But, we ask permission to do so"
tagline: 
tags : [] 
published: false
---

Someone recently asked why Teddy Hyde requests access to write to the user profile on Github when logging in. Initially I thought this was a simple mistake in configuration of the application, because we write no data back into Github. 

![/assets/images/2013-10-07-09-41-32-image-resized.png](/assets/images/2013-10-07-09-41-32-image-resized.png)

This is what you see when you login. Teddy Hyde asking for permission to write to your profile.

Turns out, I was wrong. We don't write to your profile. But, we have to ask for that permission.

Why?

The Github API allows access to your public SSH keys. We import those so that once we create a blog you can just clone the files and don't have to go through an onerous process of finding and uploading your SSH keys.

We only read these keys. We don't modify them or add any new ones. 

Unfortunately, the Github API requires that you ask for write access to read these keys. Strange and this seems like an oversight by Github. I would expect that you could get read only access to them, but this is not the case.

So, for now, we ask for permission to write to your profile even though we don't change anything at all. Unfortunate but true.
