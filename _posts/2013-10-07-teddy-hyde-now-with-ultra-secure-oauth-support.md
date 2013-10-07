---
layout: post 
category: 
title: "Teddy Hyde, now with ultra secure oAuth support"
tagline: 
tags : [] 
published: false
---

Now that all the excitement about Miley Cyrus twerking has died down, the good people of modern civilization have rightly returned their focus to the debate over oAuth and passwords.

![/assets/images/2013-10-07-07-55-18-image-resized.png](/assets/images/2013-10-07-07-55-18-image-resized.png)

Wait, you say, what is oAuth? You don't know?

Fortunately, you don't need to know. What you do need to know is that Teddy Hyde now uses it instead of asking for your username and password. This makes using Teddy Hyde much safer for you and makes it impossible for us to accidentally compromise losing your credentials on Github.

Previously, the app asked for your username and password. This was bad. Why? Well, you had to trust that a closed source piece of software would not send this off to a decrepit Russian bunker where they would login to Github using your credentials and upload visual basic files, ruining your reputation on Reddit. You had to trust that we would not be hacked and give out your password that way. Since the only thing you only know for sure about Teddy Hyde is that we have a horrible sense of humor, asking for this level of trust from our users never made sense.

With oAuth, you actually login to Github and then after Github has verified your identity, they send an identity token to Teddy Hyde. That means Teddy Hyde never sees your password. And, if you go to Github you can revoke that identity token without Teddy Hyde preventing it or even knowing.

Miley Cyrus probably wishes she could revoke her token identity as well. But, she is not using oAuth, unlike Teddy Hyde. 