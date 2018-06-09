![emscripten logo](media/switch_logo.png)

[![Build Status](https://travis-ci.org/kripken/emscripten.svg?branch=incoming)](https://travis-ci.org/kripken/emscripten)
[![CircleCI](https://circleci.com/gh/kripken/emscripten.svg?style=svg)](https://circleci.com/gh/kripken/emscripten)

Emscripten is an [LLVM](https://en.wikipedia.org/wiki/LLVM)-to-JavaScript compiler. It takes LLVM bitcode - which can be generated
from C/C++, using `llvm-gcc` (DragonEgg) or `clang`, or any other language that can be
converted into LLVM - and compiles that into JavaScript, which can be run on the web (or
anywhere else JavaScript can run).

Links to **demos**, **tutorial**, **FAQ**, etc: <https://github.com/kripken/emscripten/wiki>

Main project page: <http://emscripten.org>



## Revised Content

* **IndexedDB caching support**

You can enable module caching when building to WebAssembly. For example:

```
emcc file.cpp -s MODULE_CACHE="[1, 'appName']" -s WASM=1 -o QuickSort.html
```

Here you need to use the "MODULE_CACHE" parameter to specify the caching version (eg: 1) and module name (eg: 'appName'). With the module caching enabled, the corresponding "WebAssembly.Module" object will be load from the local cache directly rather than fetching it from remote server. This measure will reduce a lot of overhead caused by network request.

This option will automatically detecting the compatibility of browser's "WebAssembly structured clone" feature, and directly fetching the binary file from remote server if it was disabled.



> Note: This option can only be used on the latest Firefox and Safari by default, due to some "[concerns](https://code.google.com/p/v8/issues/detail?id=4392) ", the "structured clone for wasm modules" feature has already been disabled by default in Chrome, you need to enable it if you want to use this option on Chrome.



License
-------

Emscripten is available under 2 licenses, the MIT license and the
University of Illinois/NCSA Open Source License.

Both are permissive open source licenses, with little if any
practical difference between them.

The reason for offering both is that (1) the MIT license is
well-known, while (2) the University of Illinois/NCSA Open Source
License allows Emscripten's code to be integrated upstream into
LLVM, which uses that license, should the opportunity arise.

See `LICENSE` for the full content of the licenses.
