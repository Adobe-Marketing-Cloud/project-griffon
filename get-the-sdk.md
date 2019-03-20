# Implement SDK & Extension

To start implementing Project Griffon in your mobile app, please follow these steps.

{% hint style="warning" %}
Before you continue - ensure you have the Experience Platform SDK Core installed before proceeding. Visit [documentation](https://aep-sdks.gitbook.io/docs/getting-started/create-a-mobile-property) for getting started with the Experience Platform SDK.
{% endhint %}

## Implement SDK extension

{% tabs %}
{% tab title="iOS" %}
### 1. Implement the SDK

Extract the beta zip file named  `ios-builds-0.0.7-alpha-Griffon.zip` . The extracted zip will have the following folder structure:

* /iOS
  * /include
    * Will contain the header files required \(\*.h\).
  * the `.a` file for the library
* In the Xcode project create a new Group, and then drag the iOS folder under the group. And verify the following:
  * `The Copy Items if needed checkbox` is selected.
  * `Create groups` is selected.
  * In the`Add to targets` section select all the targets that need the SDK.

### 2. Implement the Bridge

Extract the beta zip file named v5-ios-builds-0.0.6-alpha-ACPGriffonBridge.zip. Add the iOS folder similar to the instructions as above. Then,

* Select your project from the `Project Navigator`, select your App from the `TARGETS` frame, then select the `General`tab at the top of the window.
* In the `Link Binary With Libraries` section, click the `+` link and add the following frameworks and libraries: `UIKit`, `SystemConfiguration`, `WebKit`, `UserNotifications`, `libsqlite3.0`, `libc++`, `libz`.
{% endtab %}
{% endtabs %}

## Register with Core

Registering the extension with Core will send Experience Platform SDK events an active session. To start using the extension library, please register the extension with the [Mobile Core](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core).

{% tabs %}
{% tab title="iOS" %}
#### Objective-C

```objectivec
[ACPGriffonBridge registerExtension];
```
{% endtab %}
{% endtabs %}

## Start session

Once the extension has been registered, you may begin a session using the following API. The `startSession` API accepts a deep link in order to begin a session. The SDK will display a pin authentication overlay in the app to proceed.

{% tabs %}
{% tab title="iOS" %}
#### Objective-C

```objectivec
- (BOOL)application:(UIApplication *)app openURL:(NSURL *)url options:(NSDictionary<UIApplicationOpenURLOptionsKey,id> *)options {
    [ACPGriffonBridge startSession:url];
    return false;
}
```
{% endtab %}
{% endtabs %}

## End session

A session may be ended in the app interface by touching the floating indicator and selecting _end session_. 



