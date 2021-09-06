# Page Object Model

The Page Object Model of UI Testing is a fantastic way of logically recreating the application with a shadow API that allows you to quickly and easily write UI Tests that make sense. For more information about how the Page Object Model works, be sure to check out [this video](https://www.youtube.com/watch?v=4VR861BWkiU) from #XamDevSummit 2019 by Sweeky.

## Setting up your first Page

To start let's make a few assumptions. For this we'll assume that you have a page in your app's codebase called `LoginPage`. That page has two text fields, one for the username and one for the password. Finally it has a Login button that when pressed will result in some sort of behavior. To start we'll create a new class in our UI Test project that is also called `LoginPage`. That class will inherit from Xappium's `BasePage`, and provide the name of an element the will only exist on that page. Next we'll create some additional constants for the other elements on the Page that we'll want to interact with like the following:

```csharp
public class LoginPage : BasePage
{
    protected override string Trait => LoginButton;

    private const string UsernameEntry = nameof(UsernameEntry);
    private const string PasswordEntry = nameof(PasswordEntry);
    private const string LoginButton = nameof(LoginButton);
}
```

Now that we have a page to work with, we'll need to add some methods to make it easier to work with when we write our tests. We can start with a method to enter a username. After we enter the username we can take a screenshot and finally make an assertion that the text in the returned element matches the username that we entered.

```csharp
public LoginPage EnterUsername(string username)
{
    var element = Engine.EnterText(UsernameEntry, username);
    Engine.Screenshot($"Entered username {username}");
    Assert.Equal(username, element.Text);
    return this;
}
```

Now that we can enter a username, we will want to enter a password into the password field. Note that here we do not do an assertion that the element's text matches the password we provided. This is due to a limitation of Appium that just like your user it is not able to read the text from a protected input field that displays something like `********`.

```csharp
public LoginPage EnterPassword(string password)
{
    var element = Engine.EnterText(PasswordEntry, password);
    Engine.Screenshot("EnteredPassword");
    return this;
}
```

Finally we'll add a method to tap the login button. You will notice that unlike the first two methods which provided a fluent API to return the LoginPage, this method simply returns void. This is, itself part of the PageObjectModel in which actions which should terminate the presence of the Page should return a void.

```csharp
public void TapLoginButton()
{
    Engine.Tap(LoginButton);
    Engine.Screenshot("Tapped Login Button");
}
```