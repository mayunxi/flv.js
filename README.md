
flv.js  [![npm](https://img.shields.io/npm/v/flv.js.svg?style=flat)](https://www.npmjs.com/package/flv.js)
======
An HTML5 Flash Video (FLV) Player written in pure JavaScript without Flash. LONG LIVE FLV!

This project relies on [Media Source Extensions][] to work.

## Overview
flv.js works by transmuxing FLV file stream into ISO BMFF (Fragmented MP4) segments, followed by feeding mp4 segments into an HTML5 `<video>` element through [Media Source Extensions][] API.

flv.js is written in [ECMAScript 6][], transpiled into ECMAScript 5 by [Babel Compiler][], and bundled with [Browserify][].

[Media Source Extensions]: https://w3c.github.io/media-source/
[hls.js]: https://github.com/dailymotion/hls.js
[ECMAScript 6]: https://github.com/lukehoban/es6features
[Babel Compiler]: https://babeljs.io/
[Browserify]: http://browserify.org/

## Demo
[http://bilibili.github.io/flv.js/demo/](http://bilibili.github.io/flv.js/demo/)

## Features
- FLV container with H.264 + AAC / MP3 codec playback
- Multipart segmented video playback
- HTTP FLV low latency live stream playback
- FLV over WebSocket live stream playback
- Compatible with Chrome, FireFox, Safari 10, IE11 and Edge
- Extremely low overhead, and hardware accelerated by your browser!

## Installation
```bash
npm install --save flv.js
或者
git clone 
```

## Build
```bash
sudo npm install          # install dev-dependences
sudo npm install -g gulp  # install build tool
gulp release         # packaged & minimized js will be emitted in dist folder,如果出现/usr/bin/env: "node": 没有那个文件或目录，sudo ln -s /usr/bin/nodejs /usr/bin/node
```

[cnpm](https://github.com/cnpm/cnpm) mirror is recommended if you are in Mainland China.

## CORS
If you use standalone video server for FLV stream, `Access-Control-Allow-Origin` header must be configured correctly on video server for cross-origin resource fetching.

See [cors.md](docs/cors.md) for more details.

## Getting Started
```html
<script src="flv.min.js"></script>
<video id="videoElement"></video>
<script>
    if (flvjs.isSupported()) {
        var videoElement = document.getElementById('videoElement');
        var flvPlayer = flvjs.createPlayer({
            type: 'flv',
            url: 'http://example.com/flv/video.flv'
        });
        flvPlayer.attachMediaElement(videoElement);
        flvPlayer.load();
        flvPlayer.play();
    }
</script>
```

## Limitations
- MP3 audio codec is currently not working on IE11 / Edge
- HTTP FLV live stream is not currently working on all browsers, see [livestream.md](docs/livestream.md)

## Multipart playback
You only have to provide a playlist for `MediaDataSource`. See [multipart.md](docs/multipart.md)

## Livestream playback
See [livestream.md](docs/livestream.md)

## API and Configuration
See [api.md](docs/api.md)

## Debug
```bash
npm install          # install dev-dependences
npm install -g gulp  # install build tool
npm run dev          # with incremental compile and auto reload
```

## Design
See [design.md](docs/design.md)

## License
```
Copyright (C) 2016 Bilibili. All Rights Reserved.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```
