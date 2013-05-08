---
layout: page
category: 
tagline: 
tags : [] 
published: true
title: "Using Hyde Transforms"
---

Hyde Transforms allow you to customize the Teddy Hyde editor. Technically a Hyde Transform is a bit of JSON which the Teddy Hyde editor loads and then adds menu items which allow you to do insertions with predefined text snippets and more. Hyde Transforms support placeholders and filters to allow you to dynamically build powerful extensions into the Teddy Hyde editor.

Use these rake tasks (available from the [Rakefile](https://github.com/xrd/blog.teddyhyde.com/blob/gh-pages/Rakefile) in a [Teddy Hyde created Jekyll blog](https://teddyhyde.com)) to learn more.

    rake teddyhyde:transform           # Add a new Teddy Hyde transform
    rake teddyhyde:transform_examples  # Print teddyhyde transform examples

To get to transforms, load a file and then click on the "Hyde Transform..." menu item. 

![/assets/images/2013-04-05-08-48-58-image-resized.png](/assets/images/2013-04-05-08-48-58-image-resized.png)

You'll see all valid transforms listed there.

In this [example](https://github.com/xrd/blog.teddyhyde.com/blob/gh-pages/_hyde/transforms.json), after clicking on "Hyde Transform..." I see two transforms, "Colored Image" (which prompts me to pick an image and then prompts for a border color to apply to that image) and "Angular FooCtrl" (which just inserts some HTML that could be used to apply an [AngularJS](http://angularjs.org) controller)

![/assets/images/2013-05-08-06-53-26-image-resized.png](/assets/images/2013-05-08-06-53-26-image-resized.png)

The simplest transform is just an insert. When you choose this one in the menu, it will insert the text in the code attribute of the JSON. Here is an example.

        {
            "code": "<div ng-controller=\"FooCtrl\"> &#123; #123; myVar &#123; &#123; <div>\n", 
            "name": "Angular FooCtrl", 
            "prompt": null, 
            "type": "insert", 
            "version": 1
        }
    ]

You can prompt the user for information. Teddy Hyde will prompt the user and then replace the text with the placeholder &#123;&#123;PROMPT&#125;&#125;.

    "code": "You answered &#123;&#123;PROMPT&#125;&#125; (the correct answer is 44)",
    "prompt": "At what age did Robert Louis Stevenson die?"

You can insert text as we saw above. You can also choose an image and then insert code with the image URI. For example:

    "code": "<img src="&#123;&#123;IMAGE&#125;&#125;",
    "type": "image", 

You can run filters on the results, for example, when you want to escape HTML or URL encode it. Valid filters are "html", "url", "escdblquotes".

    "code": "<img src="http://imagegeneratorserver.com/?url=&#123;&#123;IMAGE|url&#125;&#125;/>",
    "type": "image", 

You can even run a regex search and replace. For example, imagine you want to swap png extensions for jpg.

    "code": "<img src="&#123;&#123;IMAGE|/\.png$/\.jpg/&#125;&#125;"/>",


### Caveats ###

Filters are case sensitive. html is different than HTML.

Spacing is significant. Beware of doing &#123; &#123; PROMPT
&#125; &#125; as opposed to 
&#123;&#123;PROMPT&#125;&#125;

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

{% share = "[{{PROMPT}}]({{URL}})" %}

    source: "share",
    type: "url",
    code: "{{share}}",
    prompt: "Give this link a caption"

This might allow you to share a URL into Teddy Hyde from another application and then insert it as a link into your markdown text.

### Context sensitive transforms based on file type

Right now Teddy Hyde only really knows about Markdown. Long term I would like to support other markdown formats. So, it would be nice to filter
your transforms and only show tose relevant for that particular file type (probably based on extension). 
Add a field to transform for extension and only enable if extension matches.

    code: ".div",
    filetype: "haml"

For example, let's only do this if we are editing a HAML file.
