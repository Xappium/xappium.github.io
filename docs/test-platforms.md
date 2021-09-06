# Supported Test Frameworks

Unlike Xamarin.UITest, Xappium was developed with the specific intent that you should be able to pick and choose which test framework you would like to use. When developing Xappium we used some inspiration from [Fluent Assertions](https://github.com/fluentassertions/fluentassertions) to ensure that Xappium could properly integrate with whichever test framework you wanted to use. Below are a list of each of the supported frameworks:

| Framework | Status | Screenshots |
|:----:|-----|:---:|
| MS Test | ![Nuget](https://img.shields.io/nuget/v/Xappium.UITest.MSTest?style=plastic) | Supported |
| MSpec | Technically Supported | Not Supported |
| NSpec | Technically Supported | Not Supported |
| NUnit | ![Nuget](https://img.shields.io/nuget/v/Xappium.UITest.NUnit?style=plastic) | Supported |
| xunit | ![Nuget](https://img.shields.io/nuget/v/Xappium.UITest.Xunit?style=plastic) | Not Supported by Framework |

## Screenshots

Xappium itself does support providing screenshots for your unit tests. Not all Unit Test frameworks however support attaching files such as a screen shot to a specific test. For those frameworks that do support it, you may have the added benefit that upon publishing the test results, some build platforms such as Azure DevOps will provide you the screenshots as part of test results.
