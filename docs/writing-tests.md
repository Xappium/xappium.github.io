# Writing UI Tests

While you do not specifically have to follow the [Page-Object-Model](page-object-model.md), Xappium was built with this being the preferred method of testing your apps. If you do not understand it, please take a moment to familiarize yourself with it before continuing. Xappium additionally supports support libraries for each of the major [Unit Test frameworks](test-platforms.md), each support library contains a base helper class that understands the specific framework and how to properly initialize and cleanup after a test.

## Writing your first test

One of the reasons why we recommend the Page Object Model is that it keeps your code clean. In fact writing a simple test to validate that your App Launches as just this simple...

```csharp
public class AppTests : XappiumTestBase
{
    [Fact]
    public void AppLaunches()
    {
        new LoginPage();
    }
}
```

When using a Page, the BasePage will look for the specified trait and make the Assertion that you are on that given Page. By simply specifying the Page that you expect on startup you can validate quickly and easily that your App did in fact launch and even get a screenshot for free.

## Using Variables

Part of the Xappium Configuration is a settings Dictionary that allows you to specify Key Value Pairs that you can use within your tests. For example you may want to provide a Username and Password which can be supplied by the settings to ensure that they can be easily passed in at runtime while avoiding checking in these sorts of sensitive values.

```csharp
[Fact]
public void LogsIntoMainPage()
{
    new LoginPage()
        .EnterUsername(Engine.Settings["username"])
        .EnterPassword(Engine.Settings["password"])
        .TapLoginButton();

    new MainPage()
        .ValidateWelcomeMessage();
}
```