---
layout: page
category: 
tagline: 
title: How Teddy Hyde works under the hood
tags : [] 
published: false
---

# A brief overview of Teddy Hyde for nerds #

Thinking of digging into the editor code to contribute? This document will get you started.


1. A user logs in
2. Teddy Hyde logs in and grabs an auth token. This token is stored in the preferences of the app so each activity can use it easily.
1. Once login is successful, the app starts the repository activity. This