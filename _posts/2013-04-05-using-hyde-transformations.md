---
layout: page
category: 
tagline: 
tags : [] 
published: true
---

Hyde Transforms allow you to customize your editor. Technically a Hyde transform is a bit of JSON which the Teddy Hyde editor loads and precesses when it loads

![/assets/images/2013-04-05-08-48-58-image-resized.png](/assets/images/2013-04-05-08-48-58-image-resized.png)

![/assets/images/2013-04-05-03-29-52-image-resized.png](/assets/images/2013-04-05-03-29-52-image-resized.png)


        {
            "code": "<div ng-controller=\"FooCtrl\">{{myVar}}</div>\n", 
            "name": "Angular FooCtrl", 
            "prompt": null, 
            "type": "insert", 
            "version": 1
        }
    ]

## the future ##

### third party data services

    source: http://foo.com
    array: true
    type: insert

### Addressable sharing intents

Add ability to recognize a shared URL coming into Teddy Hydeand do something with it in your transform.

### Context sensitive transforms based on file type

add a field to transform for extension and only enable if extension matches.
