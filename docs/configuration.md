# UI Test Configuration

Xappium makes every attempt to make configuration as easy as possible. It is important to recognize that this may allow you to make a test configuration as simple or complex as your needs require.

> [!Note]
> If you are using the Xappium CLI most of the configuration values can be omitted as they will be automatically provided by the CLI.

## Using the uitest.json

By default Xappium looks for a file called `uitest.json`. This file can either be an EmbeddedResource in the UI Test project, or can be copied to the output directory. If the `uitest.json` is embedded it will merge with one that was copied to the output directory. This functionality may provide you the ability to provide specific overrides for iOS or Android by changing the build configuration to select something like `android-uitest.json` to Embed. It's important to note that when looking for an Embedded uitest.json, it only needs to end with uitest.json, and it does not need to be named exactly as `uitest.json`.

To make it easier to configure the `uitest.json` has been setup with a schema to make it easier for you to get intellisense when creating the file manually.

```json
{
  "$schema": "https://xappium.github.io/uitest.schema.json"
}
```

### Overriding Xappium default Capabilities for Appium

Appium expresses several "Capabilities" for each platform.

| Platform | Specific Capabilities |
|:----:|:---:|
| Generic Appium | [Docs](https://appium.io/docs/en/writing-running-appium/caps/) |
| XCUITest | [ReadMe](https://github.com/appium/appium-xcuitest-driver#capabilities) |
| Espresso | [ReadMe](https://github.com/appium/appium-espresso-driver#capabilities) |

In the event that you require an additional capability or should you need to completely override the capability that Xappium provides, you can do so by adding them to the capabilities dictionary in the `uitest.json` like the following:

```json
{
  "capabilities": {
    "showGradleLog": "true"
  }
}
```

## Using Environment Variables

In addition to using the json file to configure your tests, you can additionally configure your tests using environment variables.

- UITEST_APPIUMSERVER
- UITEST_DEVICENAME
- UITEST_OSVERSION
- UITEST_UDID
- UITEST_PLATFORM
- UITEST_APP_PATH
- UITEST_APPID
- UITEST_SCREENSHOT_PATH
- UITEST_ADDITIONAL_CAPABILITIES