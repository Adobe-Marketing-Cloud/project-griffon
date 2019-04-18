# Implement the SDK and the extension

To implement Project Griffon in your mobile app, complete the following steps:

{% hint style="warning" %}
Before you continue, you must install the Experience Platform SDK Core extension. To get started with the Experience Platform SDK, see [Overview](https://app.gitbook.com/@aep-sdks/s/docs/). For information about installing the Mobile Core extension, see [Mobile Core](https://app.gitbook.com/@aep-sdks/s/docs/using-mobile-extensions/mobile-core).
{% endhint %}

## Implement the SDK extension

{% tabs %}
{% tab title="iOS" %}
### 1. Implement the SDK

Extract the `ios-builds-0.0.3-alpha-Straightpipe.zip`  beta zip file.  
  
The extracted zip has the following folder structure:

* /iOS
  * /include
    * Contains the required header files \(\*.h\).
  * the `.a` file for the library
* In the Xcode project, create a new Group, drag the iOS folder under the group, and verify the following:
  * **The Copy Items if needed checkbox** is selected.
  * **Create groups** is selected.
  * In the **Add to targets** section, all the targets that need the SDK are selected.

### 2. Implement the Bridge

Extract the `v5-ios-builds-0.0.3.1-alpha-ACPStraightpipeBridge.zip` beta zip file. 

Add the iOS folder similar to the instructions in step 1 above. 

Complete the following tasks:

1. Select your project from the `Project Navigator`, select your App from the `TARGETS` frame, and select the **General** tab at the top of the window.
2. In the **Link Binary With Libraries** section, click the **+** link and add the following frameworks and libraries: 

`UIKit`, `SystemConfiguration`, `WebKit`, `UserNotifications`, `libsqlite3.0`, `libc++`, `libz`.
{% endtab %}
{% endtabs %}

## Register with Core

Registering the extension with Core sends an active session to the Experience Platform SDK events. To start using the extension library, register the extension with the [Mobile Core](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core).

{% tabs %}
{% tab title="iOS" %}
#### Objective-C

```objectivec
[ACPStraightpipeBridge registerExtension];
```
{% endtab %}
{% endtabs %}

## Start the session

After the extension has been registered, you can begin a session by using the following API. The `startSession` API accepts a deep link to begin a session. To proceed, the SDK displays a pin authentication overlay in the app.

{% tabs %}
{% tab title="iOS" %}
#### Objective-C

```objectivec
- (BOOL)application:(UIApplication *)app openURL:(NSURL *)url options:(NSDictionary<UIApplicationOpenURLOptionsKey,id> *)options {
    [ACPStraightpipeBridge startSession:url];
    return false;
}
```
{% endtab %}
{% endtabs %}

## End the session

A session can be ended in the app interface by touching the floating indicator and selecting **end session**. 



