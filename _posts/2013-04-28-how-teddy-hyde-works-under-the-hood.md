---
layout: page
category: 
tagline: 
title: How Teddy Hyde works under the hood
tags : [] 
published: true
---

## A brief overview of Teddy Hyde for nerds ##

Thinking of digging into the editor code to contribute? This document will get you started.

1. A user logs in. Teddy Hyde logs in and grabs an auth token. This token is stored in the preferences of the app so each activity can use it easily.
1. Once login is successful, the app starts the repository activity. This activity uses the token retrieved from the Github API to grab a list of repositories for display in a list view.
1. The specialized list view adapter sorts the repositories by name, putting those with names ending in github.io or in .com first. Since Teddy Hyde is first and foremost a Jekyll blog editor it expects you will want to see those at the top of your list.
1. 