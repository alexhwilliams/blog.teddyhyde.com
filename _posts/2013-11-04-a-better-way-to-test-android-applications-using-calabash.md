---
published: true
layout: post
tags: calabash ruby android chromebook
title: "A better way to test Android applications using Calabash"
---

## A video showing the power of calabash.

This video shows calabash testing my app which uses oAuth to login and many parts of the GitHub API. 
No manual operations were performed; this was all automated using Calabash for Android.

<object width="480" height="360"><param name="movie" value="//www.youtube.com/v/kIJrnnFeAiY?version=3&amp;hl=en_GB"></param><param name="allowFullScreen" value="true"></param><param name="allowscriptaccess" value="always"></param><embed src="//www.youtube.com/v/kIJrnnFeAiY?version=3&amp;hl=en_GB" type="application/x-shockwave-flash" width="480" height="360" allowscriptaccess="always" allowfullscreen="true"></embed></object>

## The barriers to testing complex next generation Android applications

This post details using calabash to run automated tests on Android applications (though calabash works with iOS as well). Calabash is simply the easiest way to test complex mobile applications and I show how to test my app, <a href="https://play.google.com/store/apps/details?id=com.EditorHyde.app">Teddy Hyde</a>
, an Android editor for Jekyll blogs that uses the GitHub API and oAuth login. Testing applications which make use of APIs is a complex issue primarily because you are hitting a third party site and then layering your logic on top, and oAuth is a different bird with the same external coupling; these two requirements of this app, namely reliance on external services, confounded my testing attempts before finding calabash.

As Teddy Hyde has grown over the past ten months, the internal complexity has grown as well. I'm proud 
of everything offered by this little Android editor for Jekyll blogs: Markdown and Asciidoc preview with just
a swipe, oAuth login and 2-factor authentication support for the highest level of security with 
your GitHub account, image upload and resizing, editor extension using "Hyde Transforms." And, making sure 
all the features work after new features are introduced becomes a QA problem; it simply is not easy to make sure new features
don't break other working features. Naturally I want to automate testing as much as possible.

Android is well designed and very test friendly. Thinking about components as "activities" and then parameterizing them
with data (called "bundles" supplied via a launching "intent") means you are designing components which 
can easily be tested inside a container. Yet, the recent changes to the tooling environments, namely Android Studio and 
gradle, have relegated the implementation and integration of testing to the bottom of the to-do list. It simply
is not easy or obvious right now to add tests, especially UI tests via Robotium. 

## Calabash makes testing easy and powerful

I recently discovered Calabash, and it has changed my relationship to testing Android applications. Here is an easy to use android (and iOS) testing harness
that works using Cucumber feature scripts. It is simple to get started with and has immense power because
it is a pure Ruby testing DSL. Ruby makes testing much easier than writing in Java. Java is a great language
for high performance applications, but a poor language for writing test scripts, where terseness and simplicity trump
execution speed. Calabash succeeds because it is simple and offers the full expression that comes from ruby and
all the available ruby libraries.

Calabash was developed by LessPainful, recently acquired by Xamarin. They have a great user group on Google. And, I did not feel that there were good introductions to people new to calabash, especially those new to Cucumber testing. I am
embarassed to say that as a long time rails developer I never had used Cucumber (rspec has always been my cup of tea). So, this post 
attempts to provide a gentle introduction to calabash, cucumber and testing the UI of your Android applications. Teddy
Hyde uses oAuth for logging into your GitHub account, so this is a real world example of mixing vanilla UI components
like native buttons with UI components inside a WebView like you'll find if your application uses oAuth for authentication
outside of your app.

## Cucumber and Calabash

To start, what is Cucumber? And, what is Calabash? Cucumber is a method of writing tests, described by the authors as "behaviour driven
development with elegance and joy." It certainly makes me happy and I do agree it is elegant. A cucumber test is often
two files, the "features," (a human readable set of instructions) and the "steps," a set of code which implements the tests. For example, you 
might have a test like this:

    Feature: Add file to repository
      Scenario: As a logged in user I can add a file
        Given I start the login process

Then, you have step definitions, the code which performs these actions as a test. Your step definitions for this test might look 
like this:

    Given /I start the login process/ do
      touch "button"
    end

What this means, is there is a feature called "Add file to repository" with a scenario "as a logged in user I can add a file"
that has one step defined, "given I start the login process." And, then we have defined that step as `touch "button"`. 
`touch "button"` is calabash code to touch a button in your Android app. These steps match your features and you can do more advanced things like have a Regexp which matches and extracts parameters you then use in your steps. There is also a large library of standard steps which calabash provides for you to do the most common things involved with interacting with an Android application.

So, what's calabash? Calabash is a set of scripts and an API which setup your Android app on a real device (or emulator) and then 
runs through the tests you've defined. Setting up on your device means installing the app, and installing a test runner server
based on Robotium which can communicate clicks, scrolls, etc. Then, calabash takes your features and converts those to
Robotium commands and runs your tests.

Specifically, to run your calabash features, you would do this:

    calabash-android run ./build/apk/TeddyHyde-debug-unaligned.apk

If you have a directory called features which contains the features files described above, `calabash-android run` will run those features, using the steps defined
in the step_definitions directory inside that directory.

One thing missing for me in the documentation was "How do I figure out the step definitions without reading lots
about the entire calabash API?" In this case, you want to run calabash using the console command:

    calabash-android console ./build/apk/TeddyHyde-debug-unaligned.apk

This drops you into a shell/console session and you can play with the app, querying for buttons, or any other UI element. Once 
you have figured out the proper element, via the text or ID, you can then add it to the step definitions and 
build out your test. If you don't have IRB logging turned on, now might be a good time to do that as you'll often review that log file to extract successful commands for your step files.

The neat thing about console mode is it allows you to interact with the app normally by pressing and swiping with your meaty fingers, but also allows you to interact with the app via the calabash API. So, you can get to the place in the app you need to manually and then use the API to run automated commands you paste into your step definitions. It is like driving a car with both automatic controls and a stick shift when you need it.

## Command line friendly

I love that I can run calabash scripts from within my gradle scripts or from the calabash-android command. I can even run these while my Nexus 5 is connected to my chromebook. 

## A real world test

I am posting my scripts for testing one part of Teddy Hyde. You can model these to test other applications which use a combination of native UI elements and WebView elements like this application and which hit APIs.

{% gist 7425175 %}

I attempted to implement a cleanup() function which would hit the GitHub API and clean up my files, but did not finish this, so caveat emptor there.

## Running across multiple devices using AppThwack

I would be remiss if I did not mention an awesome service by my fellow Portlanders, <a href="http://appthwack.com">AppThwack</a>. AppThwack allows you to run test against hundreds of real devices, and they support calabash scripts. You simply upload your APK and upload a zip of your calabash directory, and AppThwack will run your calabash scripts against a battery of real devices with various screen resolutions and android versions.

![/assets/images/appthwack.png](/assets/images/appthwack.png)

Whoops! Looks like I have some bugs to fix when <a href="https://play.google.com/store/apps/details?id=com.EditorHyde.app">Teddy Hyde</a> is used on other Android devices.


## A few caveats ##

If you are running Mavericks, you might need to update Xcode using this command `xcode-select --install`
as per this link

[Installing binary gems on mavericks](http://stackoverflow.com/questions/19579640/installing-redcarpet-gem-on-mavericks)

One thing I noticed was a huge difference between running my tests on a real device as opposed to a simulator. The simulator is really slow and any network operations took a long time. You can test for UI elements appearing within a certain time and these tests often failed on the emulator but worked in the real device. For this reason there are lots of wait calls in my scripts which I need to remove, but was struggling to find a balance between a working set of tests for both simulators and real devices. Fortunately, right when I was making this post I got my new Nexus 5, so the screencast is actually done by recording a real device using the `adb -s 0222fdc60910aede shell screenrecord /sdcard/calabash.mp4`. If you do use calabash on a KitKat device, make sure you install at least calabash v0.4.16 which has the latest Robotium.jar that supports KitKat.




