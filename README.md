# Screen capture and sharing

This repo is an exploration of screen capture in browsers, including using screen capture streams in WebRTC sessions with [Twilio Video](https://www.twilio.com/docs/api/video).

You can read about these examples on the Twilio Blog:

* [Screen capture in Google Chrome](https://www.twilio.com/blog/2017/10/screen-capture-in-google-chrome.html)

## Chrome extension

In the `/extension` directory is a minimal implementation of a Chrome extension that will give access to streams from the [`chrome.desktopCapture` API](https://developer.chrome.com/extensions/desktopCapture).

## Screen capture in Chrome

In the `/chrome` directory is an HTML page that takes advantage of the extension and captures the desktop to show within a `<video>` element on the page.

*Note*

You will need to load your own version of the Chrome extension into your browser and replace `YOUR_EXTENSION_ID_HERE` with your own extension ID.

You will also need to serve the file from a local web server so that you can visit it on localhost.

## Screen capture in Firefox

In the `/firefox` directory is an HTML page that uses the `mediaDevices` API with a `mediaSource` to indicate whether to capture the screen or a window.

*Note*

You will need to load this demo over HTTPS, even locally. You can do so by configuring a local web server with a self signed certificate or by setting up [ngrok](https://ngrok.com) and using the HTTPS URL that it generates.
