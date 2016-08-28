# CJOpus
Emscripten (C++/JavaScript) bindings for libopus

A module to encode PCM data to and decode PCM data from Opus.

## Using

### OpusEncoder

```js
//Tries to mimic `node-opus` in syntax.
var encoder = new OpusEncoder( 48000, 2 );
```

### OpusEncoder#encode

```js
var PCM = getPCMDataSomehow();
var encoded = encoder.encode( PCM );
```

### OpusEncoder#decode

```js
var OPUS = getOPUSDataSomehow();
var decoded = encoder.decode( OPUS );
```

## Building

Currently in the process of getting build scripts together (also not very knowledgable about that), but the steps for generating this is as follows:

* 1. Download `libopus` (1.1.3 was used here as of Aug 6th 2016).
* 2. Configure it with Emscripten's `emconfigure` (`emconfigure ./configure`)
  * 2a. If it fails and complains about intrinsics, remove `intrinsics` related logic from the `configure` file.
* 3. Make with Emscripten's `emmake` (`emmake ./make`)
* 4. Link and compile with `emcc`.
  * 4a. The command I used: `emcc --memory-init-file 0 -O3 -g0 --llvm-opts 3 --closure 1 --llvm-lto 3  CJOpus.c opus-1.1.3/.libs/libopus.so -o CJOpus.js`

Apologies if this is a bit unorthodox.
