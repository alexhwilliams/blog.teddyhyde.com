---
layout: post
title: "Build issues with android gradle plugin 0.7"
description: ""
category: 
tags: []
published: true
---

I kept seeing this

```
Error: duplicate files during packaging of APK /Users/xrdawson/Projects/TeddyHyde/TeddyHyde/build/apk/TeddyHyde-release-unsigned.apk
       Path in archive: META-INF/NOTICE
       Origin 1: /Users/xrdawson/Projects/TeddyHyde/TeddyHyde/lib/commons-logging-1.1.1.jar
       Origin 2: /Users/xrdawson/Projects/TeddyHyde/TeddyHyde/lib/jackson-core-2.2.3.jar
You can ignore those files in your build.gradle:
    android {
      packagingOptions {
          exclude 'META-INF/NOTICE'
            }
            }
```

If I understand correctly, this is because there are files with the same name inside different jar files.

I was able to fix this using this sequence of commands:

```
for x in `ls lib`; do zip -d lib/$x META-INF/LICENSE.txt; done
for x in `ls lib`; do zip -d lib/$x META-INF/NOTICE.txt; done
for x in `ls lib`; do zip -d lib/$x META-INF/LICENSE; done
for x in `ls lib`; do zip -d lib/$x META-INF/NOTICE; done
```

These commands iterate over all files in the lib directory, using the zip command to remove that file. Compilation worked fine then.