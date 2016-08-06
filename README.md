# CJOpus
Emscripten (C++/JavaScript) bindings for libopus

This module is very experimental. It was initially created as a JavaScript alternative to [`node-opus`](https://github.com/Rantanen/node-opus) for my DiscordApp client library, [`discord.io`](https://github.com/izy521/discord.io). Because of that, a lot of settings are static. However, even though my knowledge of C/C++ is VERY limited, I do plan on making this completely customizable, so if you're a bit more savvy than I am, please submit some PRs!

Currently in the process of getting build scripts together (also not very knowledgable about that), but the steps for generating this is as follows:

* 1. Download `libopus` (1.1.3 was used here as of Aug 6th 2016).
* 2. Configure it with Emscripten's `emconfigure` (`emconfigure ./configure`)
  * 2a. If it fails and complains about intrinsics, remove `intrinsics` related logic from the `configure` file.
* 3. Make with Emscripten's `emmake` (`emmake ./make`)
* 4. Link and compile with `em++`.
  * 4a. The command I used: `em++ --bind CJOpus.cpp opus-1.1.3/.libs/libopus.so -o CJOpus.js`

Apologies if this is a bit unorthodox.
