---
title: 'Worker: messageerror event'
slug: Web/API/Worker/messageerror_event
tags:
  - API
  - Worker
  - Event
  - Reference
  - messageerror
browser-compat: api.Worker.messageerror_event
---
{{APIRef}}

The `messageerror` event is fired on a {{domxref('Worker')}} object when it receives a message that can't be deserialized.

This event is not cancellable and does not bubble.

## Syntax

Use the event name in methods like {{domxref("EventTarget.addEventListener", "addEventListener()")}}, or set an event handler property.

```js
addEventListener('messageerror', event => { });

onmessageerror = event => { };
```

## Event type

An {{domxref("MessageEvent")}}. Inherits from {{domxref("Event")}}.

{{InheritanceDiagram("MessageEvent")}}

## Event properties

_This interface also inherits properties from its parent, {{domxref("Event")}}._

- {{domxref("MessageEvent.data")}} {{readonlyInline}}
  - : The data sent by the message emitter.
- {{domxref("MessageEvent.origin")}} {{readonlyInline}}
  - : A string representing the origin of the message emitter.
- {{domxref("MessageEvent.lastEventId")}} {{readonlyInline}}
  - : A string representing a unique ID for the event.
- {{domxref("MessageEvent.source")}} {{readonlyInline}}
  - : A `MessageEventSource` (which can be a {{domxref("WindowProxy")}}, {{domxref("MessagePort")}}, or {{domxref("ServiceWorker")}} object) representing the message emitter.
- {{domxref("MessageEvent.ports")}} {{readonlyInline}}
  - : An array of {{domxref("MessagePort")}} objects representing the ports associated with the channel the message is being sent through (where appropriate, e.g. in channel messaging or when sending a message to a shared worker).

## Examples

Create a worker, and listen for `message` and `messageerror` events using [`addEventListener()`](/en-US/docs/Web/API/EventTarget/addEventListener):

```js
// main.js

const worker = new Worker("static/scripts/worker.js");

worker.addEventListener("message", (event) => {
    console.error(`Received message from worker: ${event}`);
});

worker.addEventListener("messageerror", (event) => {
    console.error(`Error receiving message from worker: ${event}`);
});
```

The same, but using the `onmessageerror` event handler property:

```js
// main.js

const worker = new Worker("static/scripts/worker.js");

worker.onmessage = (event) => {
    console.error(`Received message from worker: ${event}`);
};

worker.onmessageerror = (event) => {
    console.error(`Error receiving message from worker: ${event}`);
};
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [`Worker.postMessage()`](/en-US/docs/Web/API/Worker/postMessage)
- Related events: [`message`](/docs/Web/API/Worker/message_event)
