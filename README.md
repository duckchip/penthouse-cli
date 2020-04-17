# penthouse-cli

> Cli command for penthouse

[![NPM version][npm-image]][npm-url]
[![Build Status][travis-image]][travis-url]
[![Downloads][dlcounter-image]][npm-url]

## About

This is a CLI package for [penthouse](https://www.npmjs.com/package/penthouse)

## Usage
```
yarn add --dev penthouse-cli
```
(or `npm install`, if not using [yarn](https://yarnpkg.com))

### Basic command

```
penthouse --url https://sometestwebsite.unicorn --css pub/static/some-css-file.css --width 900 --height 1890 --ouput pub/static/critical.css
```

## Options
Some options are left out. 

Only `url` and `cssString` are required - all other options are optional. Note that the html file found via `url` is expected to be styled; `penthouse` does not inject any styles, it just uses `cssString` (or `css`) to prune into critical css.

| Name             | Type               | Default | Description   |
| ---------------- | ------------------ | ------------- |------------- |
| url           | `string` | | Accessible url. Use `file:///` protocol for local html files. |
| cssString     | `string` | | Original css to extract critical css from |
| css           | `string` | | Path to original css file on disk (if using instead of `cssString`) |
| width         | `integer` | `1300` | Width for critical viewport |
| height        | `integer` | `900` | Height for critical viewport |
| keepLargerMediaQueries | `boolean` | `false` | Keep media queries even for width/height values larger than critical viewport. |
| timeout       | `integer` | `30000` | Ms; abort critical CSS generation after this time |
| pageLoadSkipTimeout | `integer` | `0` | Ms; stop waiting for page load after this time (for sites when page load event is unreliable) |
| renderWaitTime | `integer` | `100` | ms; wait time after page load before critical css extraction starts (also before "before" screenshot is taken, if used) |
| blockJSRequests | `boolean` | `true` | set to false to load JS (not recommended)
| maxEmbeddedBase64Length | `integer` | `1000` | characters; strip out inline base64 encoded resources larger than this |
| maxElementsToCheckPerSelector | `integer` | `undefined` | Can be specified to limit nr of elements to inspect per css selector, reducing execution time.
| userAgent | `string` | `'Penthouse Critical Path CSS Generator'` | specify which user agent string when loading the page |
| strict | `boolean` | `false` | Make Penthouse throw on errors parsing the original CSS. Legacy option, not recommended. |