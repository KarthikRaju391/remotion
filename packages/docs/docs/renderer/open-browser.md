---
image: /generated/articles-docs-renderer-open-browser.png
title: openBrowser()
id: open-browser
crumb: "@remotion/renderer"
---

_Available since v3.0 - Part of the `@remotion/renderer` package._

Opens a Chrome or Chromium browser instance. By reusing an instance across [`renderFrames()`](/docs/renderer/render-frames), [`renderStill()`](/docs/renderer/render-still), [`renderMedia()`](/docs/renderer/render-media) and [`getCompositions()`](/docs/renderer/get-compositions) calls, you can save time by not opening and closing browsers for each call.

```ts
const openBrowser: (
  browser: Browser,
  options: {
    shouldDumpIo?: boolean;
    browserExecutable?: string | null;
    chromiumOptions?: ChromiumOptions;
  }
) => Promise<puppeteer.Browser>;
```

## Arguments

### `browser`

Currently the only valid option is `"chrome"`. This field is reserved for future compatibility with other browsers.

### `options?`

_optional_

An object containing one or more of the following options:

#### `shouldDumpIo?`

_optional_

If set to `true`, logs and other browser diagnostics are being printed to standard output. This setting is useful for debugging.

#### `browserExecutable?`

_optional_

A string defining the absolute path on disk of the browser executable that should be used. By default Remotion will try to detect it automatically and download one if none is available. If `puppeteerInstance` is defined, it will take precedence over `browserExecutable`.

#### `chromiumOptions?`

_optional_

Allows you to set certain Chromium / Google Chrome flags. See: [Chromium flags](/docs/chromium-flags).

:::note
Chromium flags need to be set at browser launch. If you pass an instance to SSR APIs like [`renderMedia()`](/docs/renderer/render-media), the `chromiumOptions` option of that API will not apply, but rather the flags that have been passed to `openBrowser()`.
:::

## See also

- [Source code for this function](https://github.com/remotion-dev/remotion/blob/main/packages/renderer/src/open-browser.ts)
- [Server-Side rendering](/docs/ssr)
