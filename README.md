# Screen capture and sharing

This repo is an exploration of screen capture in browsers, including using screen capture streams in WebRTC sessions with [Twilio Video](https://www.twilio.com/docs/api/video).

## Screen capture in browsers

The standards version of capturing a screen from the browser is to use the `navigator.mediaDevices.getDisplayMedia()` function. You can see a simple example of this in the `/html-example` directory.

## Screen capture for video chat

In the `/video-chat` directory is a Twilio Video powered video chat application. To test this out you will need Node.js installed. `cd` to the `video-chat` directory and install the dependencies from npm.

```bash
cd video-chat
npm install
```

You will also need to configure the application by setting some environment variables. Copy the `.env.example` file to `.env` and fill in:

- Your Twilio Account Sid from your [Twilio console](https://www.twilio.com/console)
- A Twilio API Key and API Secret available from the [API Keys section of the Twilio console](https://www.twilio.com/console/video/project/api-keys)

Run the application with:

```bash
npm start
```

Visit the application at localhost:3000. Enter your name and then enter a room name. Open another browser and do the same and you will be in a video chat. Click the share screen button and you will be shown a permissions dialog. Choose the screen you want to share and accept the permissions and your screen will appear in the other video chat.

## Legacy

There are a number of legacy versions of capturing the screen in browsers. These have been kept in the repo for posterity. You can find the original versions under [the `legacy` tag](https://github.com/philnash/screen-capture/tree/legacy).

You can read about these examples on the Twilio Blog:

- [Screen capture in Google Chrome](https://www.twilio.com/blog/2017/10/screen-capture-in-google-chrome.html)
- [Screen capture in Firefox](https://www.twilio.com/blog/2017/10/screen-capture-in-firefox.html)
- [Screen capture in Microsoft Edge](https://www.twilio.com/blog/2018/05/screen-capture-in-microsoft-edge.html)
- [Screen sharing in a Twilio Video application](https://www.twilio.com/blog/2018/01/screen-sharing-twilio-video.html)
