## Applications

MOS applications act as a logical glue between hardware components, machine learning libraries and the internet. For example, you could train faces of a group of people, match it up with Twitter profiles, and have the MATRIX device read the last tweet by a recognized face. You could have your device watch for your face, and then after confirming with an NFC tag, it could unlock your front door. A wide world of possible interactions exists via MATRIX OS applications.

### Reference

More detailed information about programming MOS applications can be found in [Create An App](../examples/app-create/) and [Reference](../reference/).

### Data Flow

Sensors push to applications which push to libraries which push back to the application, which pushes to the internet, other devices and dashboards. This one-way data flow is well matched with the listener/emitter event model of JavaScript and Node. We run a function, which is asynchronous, it sends a request to a sensor, library or web call, and waits for responses. Unlike traditional request / response style APIs, these are intended to be called once and handle many responses, sometimes in parallel.

This example initializes the temperature sensor, and then handles the response.

```js
# callback style
matrix.sensor('temperature', data => {
  // data = { value: 74.123123 }
});

# promise style
matrix.sensor('temperature').then(data => {
  // data = { value: 74.123123 }
});
```
Learn more about [callbacks](https://developer.mozilla.org/en-US/docs/Glossary/Callback_function) or [promises](http://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/promise). MOS does not make true `Promise` objects, just borrows the `then` syntax.

After data is managed inside the application, it can be sent to the cloud for exporting, webhooks, analysis and to explore in the dashboard.

Learn more about [sending data](data.md)

### Dashboards

Every MOS application can display data and can be controlled by users on a highly customizable dashboard.  

Learn more about [dashboards](dashboard.md)

### Configuration driven

MOS applications use configuration files, `config.yaml`, to provide easy end-user adaptation, as well as extensive dashboard adaptability. Simple applications don't need any JavaScript and can be configuration only. Configuration is end-user accessible, and can provide unique information for individual instances of MOS applications across devices via [settings](../reference/system.md#settings).

Learn more about [configuration](configuration.md)

### Development

MOS applications are currently written in JavaScript. Python support is planned for the near future. You will need the [Command Line Interface](cli.md) installed to create, deploy and [publish](publishing.md) MOS applications.

Start learning about MOS development with [Create An App](../examples/app-create) and [Basic Dashboards](../examples/dash-create).

More details are available at the [Reference](../reference/) 

#### Development Workflow

1. `matrix create <app-name>`
1. Code and configure your app. [MOS SDK Reference](../reference/index.md)
1. `matrix use <device-id>`
1. `matrix deploy <app-name>`
1. `matrix start <app-name>`
1. Watch the app output with `matrix log`
1. When finished, publish to [MATRIX App Store](http://apps.matrix.one) with `matrix publish <app-name>`
