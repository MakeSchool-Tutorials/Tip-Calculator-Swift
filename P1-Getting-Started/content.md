1. Open _Xcode_
1. From the `File` menu, select `New` and then `Project`
1. Under `iOS` select `Application` and then select `Single View Application` and click `Next`
1. Enter `TipPro` for `Product Name`.
1. For `Organization Name` you can enter your name, your fake company name, or `Make School`
1. For `Organization Identifier`, you use a reverse domain name style base for your apps. If you own `supercoolsecretstudios.com` you would put `com.supercoolsecretstudios`. If you don't own a domain name, feel free to put `com.makeschool` for this project.
1. Select `Swift` as the `Language` and `iPhone` as the `Devices`
1. Make sure to select `Use Core Data` from the checkboxes below and for this tutorial, we will leave the other two boxes regarding _tests_ checked.
1. Click `Next` and navigate to the place on your computer where you keep projects. Don't worry about naming the folder or anything like that, _Xcode_ will handle it for you.
1. Keep the `Create Git Repository on My Mac` checkbox selected, and click `Create`
1. Check that your xcode project looks similar to this screenshot.

Can you feel the power? It's ok if you can't. The result on your screen can be very overwhelming at first. Parts of this software such as the _Interface Builder_ date back to 1988, and _Xcode_ itself dates back to something called _Project Builder_ first released in 1992! There is a lot of interesting history around this program you will use to build your apps. Steve Jobs lost control at Apple, built a new company called NeXT, got sued by Apple, and eventually got bought out by Apple and all the hard work of NeXT became the foundation for _Mac OS X_, _iOS_, _tvOS_ and _watchOS_.

It gets even more interesting! When Apple first let 3rd party developers (you) make iOS applications, that rich history was brought to life again. How do you ask? The first iPhone has specs that were much closer to the products released by NeXT in the late 80s and early 90s then the MacBook's of its time. All of the efficiency of UI components that were meant for computers almost 30 years ago, meant that the iPhone felt snappy every time you interacted with it! It may not have felt that way with 2G internet loading full desktop web pages, but once they were loaded, you could pan, zoom, and interact with a web page for the first time with you fingers in a way that felt natural.

As a result, writing apps for the earlier versions of `iOS` meant using manual memory management. Something that developers who are new to `iOS` may never even be exposed to. This is especially the case with writing code in `Swift`. Don't worry though, there are plenty of ways to mess up with automatic memory management too! As you progress through our tutorials, we will highlight memory based issues and teach you how to build your apps to be the best!

The last interesting point we will bring up about Xcode's roots? _XML_ and the _command line_. Every aspect of the _Xcode_ specific parts of your apps code base, are based in XML, and every project action (like building your app) can be done using command line tools included with Xcode. Why is this important? When you want to do something advanced in the future, these will come in handy. When you get a build error in _Xcode_ (that does not exist because of a warning or error), Xcode will make available the exact commands it used to build, and the output of what failed. Hopefully this is something you will not experience in your first year of using _Xcode_, but the first time it happens, remember this paragraph.
