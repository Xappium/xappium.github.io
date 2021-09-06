# Xappium UI Test

Welcome to Xappium UITest. There are a lot of options out there, and we believe Appium is pretty awesome but by itself it's really just too painful to easily write UI Tests that are largely cross platform. For those .NET developers coming from a Xamarin.Forms or .NET Maui background you're already used to writing Cross Platform apps that share nearly all of the code regardless of whether you're building an iOS or Android app. Now with Xappium you can write UI Tests leveraging the power of Appium that similarly share an abstraction layer that let you write UI Tests once.

We've done the hard work of figuring out how to tune Appium and handle any platform specific implementations of the Test Engine. Now you can focus on what matters... your tests! Additionally Xappium was built in a way that makes it easy to support which ever test framework you're used to whether that's MS Test, xunit, or NUnit. As long as it works with the `dotnet test` cli, it will work with Xappium!

## Why Use Xappium

Appium has a lot of advantages over Xamarin.UITest, however it can be complex to setup and it was not written with the idea that you have a cross platform app. This means that you may find yourself writing one UI Test project for each platform. Xappium was developed to provide an easy to use Cross Platform abstraction layer over Appium with the Xamarin / .NET MAUI developer in mind.

## Who created Xappium

Xappium was built largely by [Dan Siegel](https://github.com/sponsor/dansiegel), with collaboration and help from the .NET MAUI team including [Jon Dick](https://github.com/redth) & [Shane Neuville](https://github.com/pureween).