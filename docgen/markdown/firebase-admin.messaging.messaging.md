{% extends "_internal/templates/reference.html" %}
{% block title %}Messaging class{% endblock title %}
{% block body %}
Messaging service bound to the provided app.

<b>Signature:</b>

```typescript
export declare class Messaging 
```

## Properties

|  Property | Modifiers | Type | Description |
|  --- | --- | --- | --- |
|  [app](./firebase-admin.messaging.messaging.md#messagingapp) |  | App | The [App](./firebase-admin.app.app.md#app_interface) associated with the current <code>Messaging</code> service instance. |

## Methods

|  Method | Modifiers | Description |
|  --- | --- | --- |
|  [send(message, dryRun)](./firebase-admin.messaging.messaging.md#messagingsend) |  | Sends the given message via FCM. |
|  [sendAll(messages, dryRun)](./firebase-admin.messaging.messaging.md#messagingsendall) |  | Sends all the messages in the given array via Firebase Cloud Messaging. Employs batching to send the entire list as a single RPC call. Compared to the <code>send()</code> method, this method is a significantly more efficient way to send multiple messages.<!-- -->The responses list obtained from the return value corresponds to the order of tokens in the <code>MulticastMessage</code>. An error from this method indicates a total failure -- i.e. none of the messages in the list could be sent. Partial failures are indicated by a <code>BatchResponse</code> return value. |
|  [sendMulticast(message, dryRun)](./firebase-admin.messaging.messaging.md#messagingsendmulticast) |  | Sends the given multicast message to all the FCM registration tokens specified in it.<!-- -->This method uses the <code>sendAll()</code> API under the hood to send the given message to all the target recipients. The responses list obtained from the return value corresponds to the order of tokens in the <code>MulticastMessage</code>. An error from this method indicates a total failure -- i.e. the message was not sent to any of the tokens in the list. Partial failures are indicated by a <code>BatchResponse</code> return value. |
|  [sendToCondition(condition, payload, options)](./firebase-admin.messaging.messaging.md#messagingsendtocondition) |  | Sends an FCM message to a condition.<!-- -->See [Send to a condition](https://firebase.google.com/docs/cloud-messaging/admin/legacy-fcm#send_to_a_condition) for code samples and detailed documentation. |
|  [sendToDevice(registrationTokenOrTokens, payload, options)](./firebase-admin.messaging.messaging.md#messagingsendtodevice) |  | Sends an FCM message to a single device corresponding to the provided registration token.<!-- -->See [Send to individual devices](https://firebase.google.com/docs/cloud-messaging/admin/legacy-fcm#send_to_individual_devices) for code samples and detailed documentation. Takes either a <code>registrationToken</code> to send to a single device or a <code>registrationTokens</code> parameter containing an array of tokens to send to multiple devices. |
|  [sendToDeviceGroup(notificationKey, payload, options)](./firebase-admin.messaging.messaging.md#messagingsendtodevicegroup) |  | Sends an FCM message to a device group corresponding to the provided notification key.<!-- -->See [Send to a device group](https://firebase.google.com/docs/cloud-messaging/admin/legacy-fcm#send_to_a_device_group) for code samples and detailed documentation. |
|  [sendToTopic(topic, payload, options)](./firebase-admin.messaging.messaging.md#messagingsendtotopic) |  | Sends an FCM message to a topic.<!-- -->See [Send to a topic](https://firebase.google.com/docs/cloud-messaging/admin/legacy-fcm#send_to_a_topic) for code samples and detailed documentation. |
|  [subscribeToTopic(registrationTokenOrTokens, topic)](./firebase-admin.messaging.messaging.md#messagingsubscribetotopic) |  | Subscribes a device to an FCM topic.<!-- -->See [Subscribe to a topic](https://firebase.google.com/docs/cloud-messaging/manage-topics#suscribe_and_unsubscribe_using_the) for code samples and detailed documentation. Optionally, you can provide an array of tokens to subscribe multiple devices. |
|  [unsubscribeFromTopic(registrationTokenOrTokens, topic)](./firebase-admin.messaging.messaging.md#messagingunsubscribefromtopic) |  | Unsubscribes a device from an FCM topic.<!-- -->See [Unsubscribe from a topic](https://firebase.google.com/docs/cloud-messaging/admin/manage-topic-subscriptions#unsubscribe_from_a_topic) for code samples and detailed documentation. Optionally, you can provide an array of tokens to unsubscribe multiple devices. |

## Messaging.app

The [App](./firebase-admin.app.app.md#app_interface) associated with the current `Messaging` service instance.

<b>Signature:</b>

```typescript
get app(): App;
```

### Example


```javascript
var app = messaging.app;

```

## Messaging.send()

Sends the given message via FCM.

<b>Signature:</b>

```typescript
send(message: Message, dryRun?: boolean): Promise<string>;
```

### Parameters

|  Parameter | Type | Description |
|  --- | --- | --- |
|  message | [Message](./firebase-admin.messaging.md#message) | The message payload. |
|  dryRun | boolean | Whether to send the message in the dry-run (validation only) mode. |

<b>Returns:</b>

Promise&lt;string&gt;

A promise fulfilled with a unique message ID string after the message has been successfully handed off to the FCM service for delivery.

## Messaging.sendAll()

Sends all the messages in the given array via Firebase Cloud Messaging. Employs batching to send the entire list as a single RPC call. Compared to the `send()` method, this method is a significantly more efficient way to send multiple messages.

The responses list obtained from the return value corresponds to the order of tokens in the `MulticastMessage`<!-- -->. An error from this method indicates a total failure -- i.e. none of the messages in the list could be sent. Partial failures are indicated by a `BatchResponse` return value.

<b>Signature:</b>

```typescript
sendAll(messages: Message[], dryRun?: boolean): Promise<BatchResponse>;
```

### Parameters

|  Parameter | Type | Description |
|  --- | --- | --- |
|  messages | [Message](./firebase-admin.messaging.md#message)<!-- -->\[\] | A non-empty array containing up to 500 messages. |
|  dryRun | boolean | Whether to send the messages in the dry-run (validation only) mode. |

<b>Returns:</b>

Promise&lt;[BatchResponse](./firebase-admin.messaging.batchresponse.md#batchresponse_interface)<!-- -->&gt;

A Promise fulfilled with an object representing the result of the send operation.

## Messaging.sendMulticast()

Sends the given multicast message to all the FCM registration tokens specified in it.

This method uses the `sendAll()` API under the hood to send the given message to all the target recipients. The responses list obtained from the return value corresponds to the order of tokens in the `MulticastMessage`<!-- -->. An error from this method indicates a total failure -- i.e. the message was not sent to any of the tokens in the list. Partial failures are indicated by a `BatchResponse` return value.

<b>Signature:</b>

```typescript
sendMulticast(message: MulticastMessage, dryRun?: boolean): Promise<BatchResponse>;
```

### Parameters

|  Parameter | Type | Description |
|  --- | --- | --- |
|  message | [MulticastMessage](./firebase-admin.messaging.multicastmessage.md#multicastmessage_interface) | A multicast message containing up to 500 tokens. |
|  dryRun | boolean | Whether to send the message in the dry-run (validation only) mode. |

<b>Returns:</b>

Promise&lt;[BatchResponse](./firebase-admin.messaging.batchresponse.md#batchresponse_interface)<!-- -->&gt;

A Promise fulfilled with an object representing the result of the send operation.

## Messaging.sendToCondition()

Sends an FCM message to a condition.

See [Send to a condition](https://firebase.google.com/docs/cloud-messaging/admin/legacy-fcm#send_to_a_condition) for code samples and detailed documentation.

<b>Signature:</b>

```typescript
sendToCondition(condition: string, payload: MessagingPayload, options?: MessagingOptions): Promise<MessagingConditionResponse>;
```

### Parameters

|  Parameter | Type | Description |
|  --- | --- | --- |
|  condition | string | The condition determining to which topics to send the message. |
|  payload | [MessagingPayload](./firebase-admin.messaging.messagingpayload.md#messagingpayload_interface) | The message payload. |
|  options | [MessagingOptions](./firebase-admin.messaging.messagingoptions.md#messagingoptions_interface) | Optional options to alter the message. |

<b>Returns:</b>

Promise&lt;[MessagingConditionResponse](./firebase-admin.messaging.messagingconditionresponse.md#messagingconditionresponse_interface)<!-- -->&gt;

A promise fulfilled with the server's response after the message has been sent.

## Messaging.sendToDevice()

Sends an FCM message to a single device corresponding to the provided registration token.

See [Send to individual devices](https://firebase.google.com/docs/cloud-messaging/admin/legacy-fcm#send_to_individual_devices) for code samples and detailed documentation. Takes either a `registrationToken` to send to a single device or a `registrationTokens` parameter containing an array of tokens to send to multiple devices.

<b>Signature:</b>

```typescript
sendToDevice(registrationTokenOrTokens: string | string[], payload: MessagingPayload, options?: MessagingOptions): Promise<MessagingDevicesResponse>;
```

### Parameters

|  Parameter | Type | Description |
|  --- | --- | --- |
|  registrationTokenOrTokens | string \| string\[\] |  |
|  payload | [MessagingPayload](./firebase-admin.messaging.messagingpayload.md#messagingpayload_interface) | The message payload. |
|  options | [MessagingOptions](./firebase-admin.messaging.messagingoptions.md#messagingoptions_interface) | Optional options to alter the message. |

<b>Returns:</b>

Promise&lt;[MessagingDevicesResponse](./firebase-admin.messaging.messagingdevicesresponse.md#messagingdevicesresponse_interface)<!-- -->&gt;

A promise fulfilled with the server's response after the message has been sent.

## Messaging.sendToDeviceGroup()

Sends an FCM message to a device group corresponding to the provided notification key.

See [Send to a device group](https://firebase.google.com/docs/cloud-messaging/admin/legacy-fcm#send_to_a_device_group) for code samples and detailed documentation.

<b>Signature:</b>

```typescript
sendToDeviceGroup(notificationKey: string, payload: MessagingPayload, options?: MessagingOptions): Promise<MessagingDeviceGroupResponse>;
```

### Parameters

|  Parameter | Type | Description |
|  --- | --- | --- |
|  notificationKey | string | The notification key for the device group to which to send the message. |
|  payload | [MessagingPayload](./firebase-admin.messaging.messagingpayload.md#messagingpayload_interface) | The message payload. |
|  options | [MessagingOptions](./firebase-admin.messaging.messagingoptions.md#messagingoptions_interface) | Optional options to alter the message. |

<b>Returns:</b>

Promise&lt;[MessagingDeviceGroupResponse](./firebase-admin.messaging.messagingdevicegroupresponse.md#messagingdevicegroupresponse_interface)<!-- -->&gt;

A promise fulfilled with the server's response after the message has been sent.

## Messaging.sendToTopic()

Sends an FCM message to a topic.

See [Send to a topic](https://firebase.google.com/docs/cloud-messaging/admin/legacy-fcm#send_to_a_topic) for code samples and detailed documentation.

<b>Signature:</b>

```typescript
sendToTopic(topic: string, payload: MessagingPayload, options?: MessagingOptions): Promise<MessagingTopicResponse>;
```

### Parameters

|  Parameter | Type | Description |
|  --- | --- | --- |
|  topic | string | The topic to which to send the message. |
|  payload | [MessagingPayload](./firebase-admin.messaging.messagingpayload.md#messagingpayload_interface) | The message payload. |
|  options | [MessagingOptions](./firebase-admin.messaging.messagingoptions.md#messagingoptions_interface) | Optional options to alter the message. |

<b>Returns:</b>

Promise&lt;[MessagingTopicResponse](./firebase-admin.messaging.messagingtopicresponse.md#messagingtopicresponse_interface)<!-- -->&gt;

A promise fulfilled with the server's response after the message has been sent.

## Messaging.subscribeToTopic()

Subscribes a device to an FCM topic.

See [Subscribe to a topic](https://firebase.google.com/docs/cloud-messaging/manage-topics#suscribe_and_unsubscribe_using_the) for code samples and detailed documentation. Optionally, you can provide an array of tokens to subscribe multiple devices.

<b>Signature:</b>

```typescript
subscribeToTopic(registrationTokenOrTokens: string | string[], topic: string): Promise<MessagingTopicManagementResponse>;
```

### Parameters

|  Parameter | Type | Description |
|  --- | --- | --- |
|  registrationTokenOrTokens | string \| string\[\] |  |
|  topic | string | The topic to which to subscribe. |

<b>Returns:</b>

Promise&lt;[MessagingTopicManagementResponse](./firebase-admin.messaging.messagingtopicmanagementresponse.md#messagingtopicmanagementresponse_interface)<!-- -->&gt;

A promise fulfilled with the server's response after the device has been subscribed to the topic.

## Messaging.unsubscribeFromTopic()

Unsubscribes a device from an FCM topic.

See [Unsubscribe from a topic](https://firebase.google.com/docs/cloud-messaging/admin/manage-topic-subscriptions#unsubscribe_from_a_topic) for code samples and detailed documentation. Optionally, you can provide an array of tokens to unsubscribe multiple devices.

<b>Signature:</b>

```typescript
unsubscribeFromTopic(registrationTokenOrTokens: string | string[], topic: string): Promise<MessagingTopicManagementResponse>;
```

### Parameters

|  Parameter | Type | Description |
|  --- | --- | --- |
|  registrationTokenOrTokens | string \| string\[\] |  |
|  topic | string | The topic from which to unsubscribe. |

<b>Returns:</b>

Promise&lt;[MessagingTopicManagementResponse](./firebase-admin.messaging.messagingtopicmanagementresponse.md#messagingtopicmanagementresponse_interface)<!-- -->&gt;

A promise fulfilled with the server's response after the device has been unsubscribed from the topic.

{% endblock body %}