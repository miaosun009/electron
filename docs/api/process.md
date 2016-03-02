# process

这个 `process` 对象在Electron有的以下差异从中的一个上行 node:

* `process.type` String - Process's type, 可以是 `browser` (i.e. main process)
  or `renderer`.
* `process.versions['electron']` String - Electron的版本。
* `process.versions['chrome']` String - Chromium的版本。
* `process.resourcesPath` String - JavaScript 源代码的路径.
* `process.mas` Boolean - Mac 应用商店生成, 此值是 `true`, 对于其他生成其值为 `undefined`.

## 事件

### 事件: 'loaded'

当Electron已加载其内部初始化脚本，并开始加载 web 页或主脚本时发出。

It can be used by the preload script to add removed Node global symbols back to
the global scope when node integration is turned off:

```js
// preload.js
var _setImmediate = setImmediate;
var _clearImmediate = clearImmediate;
process.once('loaded', function() {
  global.setImmediate = _setImmediate;
  global.clearImmediate = _clearImmediate;
});
```

## Properties

### `process.noAsar`

Setting this to `true` can disable the support for `asar` archives in Node's
built-in modules.

## Methods

The `process` object has the following method:

### `process.hang()`

Causes the main thread of the current process hang.

### `process.setFdLimit(maxDescriptors)` _OS X_ _Linux_

* `maxDescriptors` Integer

Sets the file descriptor soft limit to `maxDescriptors` or the OS hard
limit, whichever is lower for the current process.
