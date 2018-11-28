# [AOM Analyzer](http://aomanalyzer.org)

## Quick Start

```
npm install && npm run start

Go to localhost:3000 in a browser to see the web interface
```

## URL Parameters

### Decoders / Videos

Video decoder/file pairs are constructed from a sequence of `decoder` and `file` URL parameters. For example, the URL string `decoder=A&file=X&file=Y&decoder=B&file=X` will construct 3 pairs: `A:X`, `A:Y` and `B:X`.


## Toolbar

![GitHub Logo](/img/toolbar.png)

### Video Tabs

The very top tabs let you toggle between videos. You can also use the number keys to toggle between videos.

### Current Video Quick Info

The red bar provides quick info about the current frame.

### Commands

- `Toggle Layers`: Toggles a variety of layers on/off. To understand what the color values mean in each of the layers, you have to click on individual blocks and inspect their value in the `Block Info` tab.
- `Save Image`: Save current image to a `.png` file.
- `Reset Analyzer`: Resets the analyzer state to the first frame and clears all layers.
- `Previous Frame`
- `Play / Pause`
- `Next Frame`
- `Zoom Out`
- `Zoom In`: Zooming in the entire video can slow things down quite a bit. Use the Zoom tab instead.
- `Decode 30 More Frames`: Decode 30 more frames in a background thread. This may take a while but you should still be able to use the analyzer while that is happening.
- `Share`: Creates a shortened URL to your analyzer state.

### Tabs

- `Zoom`: Click anywhere on the decoded image to zoom in on it.

- `Histograms`:
  - `Bits`: Number of bits spent.
  - `Symbols`: % of bits spent on each symbol type.
  - `Block Size`: % of pixels within a block size.
  - `Transform Size`: % of pixels within a transform size.
  - `Transform Type`: % of pixels within a transform type.
  - `Prediction Mode`: % of pixels within a prediction mode.
  - `Skip`: % of pixels skipped.

- `Block Info`: Per selected block information and accounting. (When you click on the decoded image, you'll see a orange rectangle that highlights the selected block.)
- `Frame Info`: Per frame information and accounting.

## Accounting

Both the `Block Info` and `Frame Info` tabs have an accounting section. Accounting information keeps track of the number of bits spent on each symbol in the bit stream. The accounting tables show the symbol name, the number of bits spent on that symbol within a block (or frame), the percentage relative to the total number of bits spent in the block (or frame) and the number or samples (or the number of symbols read.)

## Building JavaScript Decoders

The analyzer uses a JavaScript decoder to decode video frames and extract information out of `.ivf` files. The decoder is compiled to JavaScript using the Emscripten compiler. To build your own decoder you'll first need to install [Emscripten](https://kripken.github.io/emscripten-site/docs/getting_started/downloads.html) and then follow the directions in the [AV1 Codec Library](https://aomedia.googlesource.com/aom/#emscripten-builds). This will produce a `inspect.js` file that you can use as a decoder in the analyzer.
