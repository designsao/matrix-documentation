## Creating, deploying and running applications

> You must have installed the [CLI](../overview/cli.md) and have a registered MATRIX device for this example.

```bash
$ matrix create testApp
$ cd testApp
$ vi app.js
```

Enter this to `app.js`. It will flash the LED green for 5 seconds.

```js
matrix.led('green').render();

setTimeout(() => {
  matrix.led('black').render();
}, 5000)
```

## Deploy 
Deploy the application to your MATRIX device

```bash
# if you don't know your device id
$ matrix list devices

# select from above list
$ matrix use {deviceId}

# from still inside the testApp directory
$ matrix deploy testApp

# run the MOS application
$ matrix start testApp
```

That's it! The light should flash green.

```bash
# stop the MOS application (optional)
$ matrix stop testApp
```