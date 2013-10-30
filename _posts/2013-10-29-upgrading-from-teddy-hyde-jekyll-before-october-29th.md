---
layout: post 
category: 
title: "Upgrading from Teddy Hyde Jekyll before October 29th"
tagline: 
tags : [] 
published: true
---
If you used Teddy Hyde to generate a blog before October 29th, 2013, you can use the following commands to grab the latest CSS and structure. 

If you have made major modifications to your blog then these commands will probably overwrite your changes in bad ways. If, however, you have simply been adding posts to your repository, these updates will make your blog look much cleaner and use bootstrap 3.0.


    git remote add teddyhyde git@teddyhyde.com:teddyhyde-jekyll.git
    git fetch teddyhyde
    git merge --no-commit teddyhyde/master
    git reset HEAD _config.yml 
    git checkout -- _config.yml
    git add CNAME
    git commit -m "Merged updates"


