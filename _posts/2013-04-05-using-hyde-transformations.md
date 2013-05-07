---
layout: page
category: 
tagline: 
tags : [] 
published: true
---

Hyde Transforms allow you to customize your editor. Technically a Hyde transform is a bit of JSON which the Teddy Hyde editor loads and then adds menu items which allow you to do special insertions and more.

Use these rake tasks to learn more.

    rake teddyhyde:transform           # Add a new Teddy Hyde transform
    rake teddyhyde:transform_examples  # Print teddyhyde transform examples

To get to transforms, load a file and then click on the "Hyde Transform..." menu item. 

![/assets/images/2013-04-05-08-48-58-image-resized.png](/assets/images/2013-04-05-08-48-58-image-resized.png)

You'll see all valid transforms listed there.

The simplest transform is just an insert. When you choose this one in the menu, it will insert the text in the code attribute of the JSON. Here is an example.

        {
            "code": "<div ng-controller=\"FooCtrl\">{{myVar}}</div>\n", 
            "name": "Angular FooCtrl", 
            "prompt": null, 
            "type": "insert", 
            "version": 1
        }
    ]

You can prompt the user for information. Teddy Hyde will prompt the user and then replace the text with the placeholder {{PROMPT}}.

    "code": "You answered {{PROMPT}}",

You can insert text as we saw above. You can also choose an image and then insert code with the image URI. For example:

    "code": "<img src="{{IMAGE}}/>",
    "type": "image", 

You can run filters on the results, for example, when you want to escape HTML or URL encode it. Valid filters are "html", "url", "escdblquotes".

    "code": "<img src="http://imagegeneratorserver.com/?url={{IMAGE|url}}/>",
    "type": "image", 

You can even run a regex search and replace. For example, imagine you want to swap png extensions for jpg.

    "code": "<img src="{{IMAGE|/\.png$/\.jpg/}}/>",


## The future of Hyde Transforms ##

These are all just ideas right now. So, don't rely on this code!

### Third Party Data Services

Imagine something like this:

    source: http://foo.com
    array: true
    type: insert

Insert or choose from a dynamic service that returns JSON.

### Addressable sharing intents

Android has awesome intents. Add the ability to recognize a shared URL coming into Teddy Hyde and do something with it in your transform.

    source: "share",
    type: "url",
    code: "[{{PROMPT}}]({{URL}})
    prompt: true

This might allow you to share a URL into Teddy Hyde from another application and then insert it as a link into your markdown text.

### Context sensitive transforms based on file type

Right now Teddy Hyde only really knows about Markdown. Long term I would like to support other markdown formats. So, it would be nice to filter
your transforms and only show tose relevant for that particular file type (probably based on extension). 
Add a field to transform for extension and only enable if extension matches.

    code: ".div",
    filetype: "haml"

For example, let's only do this if we are editing a HAML file.
