---
layout: post 
category: 
title: "Teddy Hyde, now with Crashlytics"
tagline: 
tags : [] 
published: false
---

Crashlytics recently added support for Android Studio, so we attempted to install it into Teddy Hyde. It works great, providing us with detailed and beautiful crash reporting. Hopefully you as a user of Teddy Hyde will never need to know anything other than this helps us produce software with fewer bugs, but we love it.

If you are considering using Crashlytics with your Android app, we had one issue when installing it. Teddy Hyde was built using Eclipse originally and then we added a gradle build file on top of this project. Our build paths are not what gradle typically expects and this tripped up the gradle build. To fix it, we simply added the correct path to our gradle build file.

If you see these types of issues:


    /Users/xrdawson/Projects/TeddyHyde/TeddyHyde/src/com/EditorHyde/app/MainActivity.java:29: package com.crashlytics.android does not exist
    import com.crashlytics.android.Crashlytics;
                                  ^
    /Users/xrdawson/Projects/TeddyHyde/TeddyHyde/src/com/EditorHyde/app/MainActivity.java:77: cannot find symbol
    symbol  : variable Crashlytics
    location: class com.EditorHyde.app.MainActivity
            Crashlytics.start(this);
            ^

Then try adding a line like this to your build.gradle file.


    dependencies {
        compile fileTree(dir: 'lib', include: '*.jar')
        compile fileTree(dir: 'TeddyHyde/libs', include: '*.jar')
    }

