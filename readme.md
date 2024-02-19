# Streaming Markdown

**Experiment making a streaming makdown renderer *à la ChatGPT.***

## Installation

```bash
npm install streaming-markdown
```

*Or just copy **`md_stream.js`** to your project.*

## Usage

### `Stream` object

Create new markdown `Stream` by calling `stream` function with the `HTMLElement` to render to.

```js
import * as md_stream from "streaming-markdown"

const stream = md_stream.make(document.getElementById("markdown"))
```

### `write` function

Then, you can start streaming markdown to the `Stream` by calling `write` function with the chunk of markdown string.

```js
md_stream.write(stream, "# Streaming Markdown\n\n")
```

*You can write as **many times** as needed to stream the markdown.*

The parser is optimistic.
When it sees the start of an inline code block or code block,
it will immediately style the element accordingly.

E.g. "\`print("hello wor" should be displayed as `print("hello wor

While the text is streamed in, the user should be able to select the text that has already been streamed in and copy it.
*(The parser is only adding new elements to the DOM, not modifying the existing ones.)*

### `end` function

Finally, you can end the stream by calling `end` function.

It will reset the `Stream` state and flush the remaining markdown.

```js
md_stream.end(stream)
```

## TODO

- [x] Paragraphs
- [ ] Line breaks
- [x] Headers
- [x] code block with triple backticks
- [x] `inline code` with backticks
- [x] *italic* with single asterisks
- [x] **Bold** with double asterisks
- [x] _italic_ with underscores
- [x] __Bold__ with double underscores
- [ ] Escape characters (e.g. \* or \_)
- [ ] Links
- [ ] Images
- [ ] Lists
- [ ] Blockquotes
- [ ] Tables
- [ ] Html tags (e.g. `<div>`, `<span>`, `<a>`, `<img>`, etc.)