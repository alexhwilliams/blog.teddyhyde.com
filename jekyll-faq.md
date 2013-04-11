---
layout: page
category: 
tagline: 
tags : [] 
published: false
---

# Jekyll Frequently Asked Questions #

*I pushed up a bunch of changes to Github and nothing is showing!*

Are you on the correct branch? If the URL to your site is in the form something.github.io (or the old something.github. com) then your changes should be in the master branch. If your site is your own personal domain like something.com then the changes should go into the gh-pages branch.

*I have pushed up a new site but when I go to something. com github tells me no page is here*

Check these three things:
1. Have you setup DNS correctly? You should have an A record for something.com pointing to the IP address 204.232.175.78
2. Do you have a file named CNAME in your repository with the hostname as the only contents? It should look like something.com and not http://something.com
3. Are you using the gh-pages branch? This is the correct branch if you are hosting your own domain. If your site is at something.github.io then use master branch.

