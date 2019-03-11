# SDK & Extension Implementation

## Connect to a Straightpipe session

To initialize the SDK, you need to connect to an active session. After you connect, the SDK can send data to and receive data from the Straightpipe service.

To create a Straightpipe session, see [Using the Straightpipe UI](). After you create the session, you need need the details to connect to the session using the SDK.

{% tabs %}
{% tab title="Objective C" %}
```objectivec
//The "url" is the Straightpipe session URL (deeplink)  
//setup earlier. The URL is an instance of NSURL
[ACPStraightpipe startSession:url];
```
{% endtab %}

{% tab title="Swift" %}

{% endtab %}
{% endtabs %}

{% hint style="info" %}
After the `startSession` API is called with a valid Straightpipe URL, the SDK displays a dialog box in which app user can enter the session PIN or verification. 

After a valid PIN is typed in and the app user clicks **Connect**, the SDK establishes a websocket connection. The SDK uses this connection to communicate with the backend service.
{% endhint %}

## Sending data to the Straightpipe service 

The SDK enables the application to send data to a connected session via the `sendEvent` API. If a session is not active, this API does not send anything out of the client device.

{% tabs %}
{% tab title="Objective C" %}
```objectivec
id event = [[SPIEvent alloc] initWithVendor:@"com.myapp.vendor" type:@"type" payload:@{@"key": @"value"}];
[ACPStraightpipe sendEvent:event];
```
{% endtab %}

{% tab title="Swift" %}
```text

```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
The `sendEvent` API requires an event instance. For more information about a Straightpipe event, see the [SPIEvent](straightpipe-events.md#spievent-class) documentation.
{% endhint %}

## Ending a session

An active session can be closed by using the `endSession` API. After the session is inactive, no data will leave the device.

{% tabs %}
{% tab title="Objective C" %}
```objectivec
[ACPStraightpipe endSession];
```
{% endtab %}

{% tab title="Swift" %}

{% endtab %}
{% endtabs %}















