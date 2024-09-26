# Streaming *Markdown*

[![version](https://img.shields.io/npm/v/streaming-markdown?logo=npm)](https://www.npmjs.com/package/streaming-markdown) [![github](https://img.shields.io/badge/GitHub-streaming--markdown-orange?logo=github)](https://github.com/thetarnav/streaming-markdown)

**Experiment making a streaming makdown parser *à la ChatGPT.***

---

## Description

This project is a fork of the original streaming markdown project, with additional features to support tables and LaTeX rendering

## New Features

1. **Table Parsing**: It can now parse tables in your streaming markdown.
2. **LaTeX Parsing**: Mathematical expressions written in LaTeX with the delimiters: `\(...\)` , `$...\$`, `$$...\$$`, `\[...\]` with be placed in tag `<equation-block>` or `<equation_inline>` depending on the case. Also the single dollar sign `$` is not mistaken for a latex equation

## Examples
(with katex-extensions)


### Tables

It can parse tables like this:

```
| Header 1 | Header 2 |     |   Header 1 |  Header 2  |
|----------|----------|     | ---------- | ---------- |
| Cell 1   | Cell 2   | or  |    Cell 1  |  Cell 2    |
| Cell 3   | Cell 4   |     |    Cell 3  |  Cell 4    |
```

### LaTeX

It can parse equations like this 

```
Inline equation: $a^2 + b^2 = c^2$ or \(a^2 + b^2 = c^2$\)
becomes         <equation-inline>a^2 + b^2 = c^2<equation-inline>

Block equation:
$ $                                                      \[
\int_{0}^{\infty} e^{-x^2} dx = \frac{\sqrt{\pi}}{2} or \int_{0}^{\infty} e^{-x^2} dx = \frac{\sqrt{\pi}}{2}
$ $                                                      \]
becomes        <equation-block>\int_{0}^{\infty} e^{-x^2} dx = \frac{\sqrt{\pi}}{2}<equation-block>      
```
### Issues Solved partially
- Numbering of deeply listed items
- Code Block not ending at the ``` delimiter due to the condition `pending_with_char.length ===
	p.backticks_count + p.code_fence_body`
- Insertion of `<br>` tag inside headings that doesn't work as intended

## Contributing

Contributions are welcome! Feel free to open an issue or submit a pull request.
