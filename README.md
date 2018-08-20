# Screen capture and sharing

This repo is an exploration of screen capture in browsers, including using screen capture streams in WebRTC sessions with [Twilio Video](https://www.twilio.com/docs/api/video).

You can read about these examples on the Twilio Blog:

- [Screen capture in Google Chrome](https://www.twilio.com/blog/2017/10/screen-capture-in-google-chrome.html)
- [Screen capture in Firefox](https://www.twilio.com/blog/2017/10/screen-capture-in-firefox.html)
- [Screen sharing in a Twilio Video application](https://www.twilio.com/blog/2018/01/screen-sharing-twilio-video.html)

## Chrome extension

In the `/extension` directory is a minimal implementation of a Chrome extension that will give access to streams from the [`chrome.desktopCapture` API](https://developer.chrome.com/extensions/desktopCapture).

## Screen capture in Chrome

In the `/chrome` directory is an HTML page that takes advantage of the extension and captures the desktop to show within a `<video>` element on the page.

### _Note_

You will need to load your own version of the Chrome extension into your browser and replace `YOUR_EXTENSION_ID_HERE` with your own extension ID.

You will also need to serve the file from a local web server so that you can visit it on localhost.

### _Production Note_

If you wish to deploy the Chrome extension to the Chrome web store you will need to update the extension's `manifest.json` to include your own site's URL in the `externally_connectable.matches` key. You can add more than one URL as this is an array. For example:

```json
  "externally_connectable": {
    "matches": ["*://localhost/*", "https://yourdomain.com/*"]
  },
```

## Screen capture in Firefox

In the `/firefox` directory is an HTML page that uses the `mediaDevices` API with a `mediaSource` to indicate whether to capture the screen or a window.

### _Note_

You will need to load this demo over HTTPS, even locally. You can do so by configuring a local web server with a self signed certificate or by setting up [ngrok](https://ngrok.com) and using the HTTPS URL that it generates.

## Video Chat example

In the `/video-chat` directory is a Twilio Video powered video chat application. To test this out you will need Node.js installed. `cd` to the `video-chat` directory and install the dependencies from npm.

```bash
cd video-chat
npm install
```

You will also need to configure the application by setting some environment variables. Copy the `.env.example` file to `.env` and fill in:

- Your Twilio Account Sid from your [Twilio console](https://www.twilio.com/console)
- A Twilio API Key and API Secret available from the [API Keys section of the Twilio console](https://www.twilio.com/console/video/runtime/api-keys)

If you are using Chrome, make sure you have installed the extension from the `extension` directory. Find the `getUserScreen` function in `video-chat/src/index.js` and replace `YOUR_EXTENSION_ID` with the extension ID.

Run the application with:

```bash
npm start
```

If you are using Firefox, use [ngrok](https://ngrok.com) to set up a tunnel to your localhost on port 3000.

Visit the application at localhost:3000 (or your ngrok URL). Enter your name and then enter a room name. Open another browser and do the same and you will be in a video chat. Click the share screen button and you will be shown a permissions dialog. Choose the screen you want to share and accept the permissions and your screen will appear in the other video chat.
