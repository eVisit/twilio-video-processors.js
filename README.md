# Twilio Video Processors

> [!WARNING]  
> We are no longer allowing new customers to onboard to Twilio Video. Effective **December 5th, 2024**, Twilio Video will End of Life (EOL) and will cease to function for all customers. Customers may transition to any video provider they choose, however, we are recommending customers migrate to the Zoom Video SDK and we have prepared a [Migration Guide](https://developers.zoom.us/docs/video-sdk/twilio/). Additional information on this EOL is available in our Help Center [here](https://support.twilio.com/hc/en-us/articles/20950630029595-Programmable-Video-End-of-Life-Notice).

Twilio Video Processors is a collection of video processing tools which can be used with [Twilio Video JavaScript SDK](https://github.com/twilio/twilio-video.js) to apply transformations and filters to a VideoTrack.

&nbsp;&nbsp; [See it live here!](https://twilio.github.io/twilio-video-processors.js/examples/virtualbackground/)

## Features

The following Video Processors are provided to apply transformations and filters to a person's background. You can also use them as a reference for creating your own Video Processors that can be used with [Twilio Video JavaScript SDK](https://github.com/twilio/twilio-video.js).

- [Virtual Background](https://twilio.github.io/twilio-video-processors.js/classes/VirtualBackgroundProcessor.html)
- [Background Blur](https://twilio.github.io/twilio-video-processors.js/classes/GaussianBlurBackgroundProcessor.html)

## Prerequisites

* [Twilio Video JavaScript SDK](https://github.com/twilio/twilio-video.js) (v2.15+)
* [Node.js](https://nodejs.org) (v14+)
* NPM (v6+, comes installed with newer Node versions)

### Note

The **Node.js** and **NPM** requirements do not apply if the goal is to use this library as a dependency of your project. They only apply if you want to check the source code out and build the artifacts and/or run tests.

## Installation

### NPM

You can install directly from npm.

```
npm install @twilio/video-processors --save
```

Using this method, you can import `twilio-video-processors` like so:

```ts
import * as VideoProcessors from '@twilio/video-processors';
```

### Script tag

You can also copy `twilio-video-processors.js` from the `dist/build` folder and include it directly in your web app using a `<script>` tag.

 ```html
 <script src="https://my-server-path/twilio-video-processors.js"></script>
 ```

 Using this method, `twilio-video-processors.js` will set a browser global:
 
 ```ts
 const VideoProcessors = Twilio.VideoProcessors;
 ```

### Assets

In order to achieve the best performance, the VideoProcessors use WebAssembly to run TensorFlow Lite for person segmentation. You need to serve the tflite model and binaries so they can be loaded properly. These files can be downloaded from the `dist/build` folder. Check the [API docs](https://twilio.github.io/twilio-video-processors.js/interfaces/VirtualBackgroundProcessorOptions.html#assetsPath) for details and the [examples](https://github.com/twilio/twilio-video-processors.js/tree/master/examples) folder for reference.

## Usage

These processors run TensorFlow Lite using [MediaPipe Selfie Segmentation Landscape Model](https://drive.google.com/file/d/1dCfozqknMa068vVsO2j_1FgZkW_e3VWv/preview) and requires [WebAssembly SIMD](https://v8.dev/features/simd) support in order to achieve the best performance. We recommend that, when calling [Video.createLocalVideoTrack](https://sdk.twilio.com/js/video/releases/2.28.0/docs/module-twilio-video.html#.createLocalVideoTrack__anchor), the video capture constraints be set to `24 fps` frame rate with `640x480` capture dimensions. Higher resolutions can still be used for increased accuracy, but may degrade performance, resulting in a lower output frame rate on low powered devices.

## Best Practice

Please check out the following pages for best practice.

* [VirtualBackgroundProcessor](https://twilio.github.io/twilio-video-processors.js/classes/VirtualBackgroundProcessor.html)
* [GaussianBlurBackgroundProcessor](https://twilio.github.io/twilio-video-processors.js/classes/GaussianBlurBackgroundProcessor.html)
