
As Teddy Hyde has grown over the past ten months, the internal complexity has grown as well. I'm proud
of the all the capabilities of this little Android editor for Jekyll blogs: Markdown and Asciidoc preview with just
a swipe, oAuth login and 2-factor authentication support for the highest level of security with 
your GitHub account, image upload and resizing, editor extension using "Hyde Transforms." And, making sure 
all the features work after new features are introduced becomes a testability problem; it simply is not easy to make sure new features
don't break other working features.

Android is well designed to be tested. Thinking about components as "activities" and then parameterizing them
with data (called "bundles" supplied via a launching "intent") means you are designing components which 
can easily be tested inside a container. Yet, the recent changes to the tooling, namely Android Studio and 
gradle, have relegated the implementation and integration of testing to the bottom of the to-do list. It simply
is not easy or obvious about how to add tests, especially UI tests via Robotium. 

I recently discovered Calabash, and it blows my mind. Here is a easy to use android (and iOS) testing harness
that works using Cucumber feature scripts. It is simple to get started with and has immense power because
it is a pure Ruby testing. I feel this makes it much better than writing things in Java. Java is a great language
for high performance, but a poor language for writing test scripts, where terseness and simplicity trump
execution speed. Calabash succeeds because it is simple and offers the full expression that comes from ruby and
all the available ruby libraries.

Calabash was developed by LessPainful, recently acquired by Xamarin. They have a great user group. And, I did not
feel that there were good introductions to people new to calabash, especially those new to Cucumber testing. I am
embarassed as a rails developer to say I never used Cucumber (rspec has always been my cup of tea). So, this post 
attempts to provide a gentle introduction to calabash, cucumber and testing the UI of your Android applications. Teddy
Hyde uses oAuth for logging into your GitHub account, so this is a real world example of mixing vanilla UI components
like buttons with UI components inside a WebView like you'll find if your application uses oAuth for authentication
outside of your app.

To start, what is Cucumber? And, what is Calabash? Cucumber is a method of writing tests they say is "behaviour driven
development with elegance and joy." It certainly makes me happy and I do agree it is elegant. A cucumber test is often
two files, the feature (a human readable set of instructions) and a set of code which implements the tests. For example, you 
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
`touch "button"` is calabash code to touch a button in your Android app.

So, what's calabash? Calabash is a set of scripts which setup your Android app on a real device (or emulator) and then 
run through the tests you've definied. Setting up on your device means installing the app, and installing a test runner
based on Robotium which can handle clicks, scrolls, etc. Then, calabash takes your features and converts those to
Robotium commands and runs your tests.

Specifically, to run this feature, you would do this:

    calabash-android run ./build/apk/TeddyHyde-debug-unaligned.apk

If you have a directory called features, `calabash-android run` will run those features, using the steps defined
in the step_definitions directory.

One thing missing for me in the documentation was "How do I figure out the step definitions without reading lots
about the entire calabash API?" In this case, you want to run using the console command:

    calabash-android console ./build/apk/TeddyHyde-debug-unaligned.apk

This drops you into a shell and you can play with the app, querying for buttons, or any other UI element. Once 
you have figured out the proper element, via the text or ID, you can then add it to the step definitions and 
build out your test.

When I installed calabash, if you are running Mavericks, you might need to update Xcode using this command `xcode-select --install`
as per this link

http://stackoverflow.com/questions/19579640/installing-redcarpet-gem-on-mavericks

