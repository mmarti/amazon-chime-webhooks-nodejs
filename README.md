# chime

[![npm version](https://img.shields.io/npm/v/chime?style=flat-square)](https://npmjs.com/package/chime)
![size](https://img.shields.io/bundlephobia/min/chime?style=flat-square)
[![open issues](https://img.shields.io/github/issues-raw/mmarti/chime?style=flat-square)](https://github.com/mmarti/chime/issues)
[![license](https://img.shields.io/npm/l/chime?style=flat-square)](https://github.com/mmarti/chime/blob/master/LICENSE)

Send messages using webhooks for Amazon Chime.

- [Amazon Chime](https://aws.amazon.com/chime)
- [Adding webhooks to chat rooms](https://docs.aws.amazon.com/chime/latest/ug/webhooks.html)
- [Webhooks for Amazon Chime](https://docs.aws.amazon.com/chime/latest/dg/webhooks.html)

```javascript
const Chime = require('chime');

(async () => {
  try {
    await Chime.sendMessage('hello world', '<WEBHOOK_URL>');
  } catch (err) {
    // do something with err
  }
})();
```

## Class: Chime

<sup>Added in: v1.0.0</sup>

### new Chime(url[, options])

<sup>Added in: v1.0.0</sup>

- `url` `<string>` - Webhook URL
- `options` `<object>` Overridden by `room.sendMessage()` options.
  - `markdown` `<boolean>` - Use markdown syntax. **Default:** `true`
- Returns: `<Chime>`

```javascript
const room = new Chime('<WEBHOOK_URL>');
```

### Chime.sendMessage(message, url[, options])

<sup>Added in: v1.0.0</sup>

- `message` `<string>`
- `url` `<string>` - Webhook URL
- `options` `<object>`
  - `markdown` `<boolean>` - Use markdown syntax. **Default:** `true`
- Returns: `<Promise<object>>`
  - `messageId` `<string>`
  - `roomId` `<string>`

Sends message.

```javascript
const result = await Chime.sendMessage('hello world', '<WEBHOOK_URL>');

console.log(result);
// Prints something like:
// {
//   messageId: '1d048345-443a-4ad7-8247-69cf95bc5b73',
//   roomId: '3a5be182-197c-4b48-8efe-0c6d3a0f24b1'
// }
```

### room.sendMessage(message[, options])

<sup>Added in: v1.0.0</sup>

- `message` `<string>`
- `options` `<object>`
  - `markdown` `<boolean>` - Use markdown syntax.
- Returns: `<Promise<object>>`
  - `messageId` `<string>`
  - `roomId` `<string>`

Sends message.

```javascript
const result = await room.sendMessage('hello world');

console.log(result);
// Prints something like:
// {
//   messageId: '1d048345-443a-4ad7-8247-69cf95bc5b73',
//   roomId: '3a5be182-197c-4b48-8efe-0c6d3a0f24b1'
// }
```
