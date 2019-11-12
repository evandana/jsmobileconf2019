# Embedding V8 in the Real World - Stanimira Vlaeva

## Track 2 - Session 4

### What is NativeScript?

- A native app development framework using Angular, Vue, or NativeScript 'light'
- 100% native API access
- Cross-platform abstraction for widgets, UI, CSS, etc.
- NativeScript 'light'
  - A nice out-of-the-box option with functionality for most basic apps
  - ...or Vue.js
  - ...or Angular

### Native API Access

- V8 is a JavaScript engine (used in Chrome, Node, Edge, and NativeScript)
- `new android.media.MediaRecorder()`
  - This comes from a step during the build process *(Metadata Generator)*
  - Metadata is stored inside the resulting application, and provides access to underlying API classes and methods
  - `android` is a global object
  - `android.media` is a *package getter callback*
  - `android.media.MediaRecorder` is also a _package getter callback_
  - Using `MediaRecorder()` actually instantiates the object on the native side **using JNI**
  - ...And creates a JS proxy object that is returned and lives in the JS world
- Marshalling Service
  - Handles converting JS types to Java, and vice-versa
- Garbage Collection
  - The NativeScript runtime listens for the finalize callbacks when objects in V8 get deallocated, and begins retaining a **weak** reference to the native (Java) object (instead of a previously-**strong** reference), so that the garbage collector in the JVM cleans up the native side as well
  - `releaseNativeCounterpart` API exists as a way to let the system know that you would like the native system to release/deallocate the memory

### Avoiding Jank

- Building UI, performing animations, or HTTP/network requests - all sources of main thread jank
- Worker threads (based on the web workers API)
- During startup
  - JavaScript code is being loaded from the filesystem (minimize them!)
  - Parsing and compiling takes a long time
  - **Bundling** your application helps this! (Fewer FS requests ==> faster launch time)
  - **Custom startup snapshots** uses Webpack and the `mksnapshot` tool to generate architecture-specific `.blob` binary formats, which can then be embedded into your APK