# pangloss

Provides support for interlinear glosses with Markdown example lists.

## Example

The following code snippet demonstrates the most important features of
pangloss:

```markdown
As you can see in the following examples, pangloss is really easy to use:

(@) Jorge  llama             a  Maria.
    George calls-3s.PRES.IND to Maria
    `George calls Maria.'
(@) Aussi, vous pouvez          avoir    de multiples   exemples.
    also   you  can-2p.PRES.IND have.INF of multiple-PL example-PL
    `You can also have multiple examples.' {#ex:french}

You can even refer to examples, as in @ex:french.

(@) Here, the sentence doesn't require any gloss.
    {}
    {} 
```

Each example consists of three lines: an original, a word-by-word analysis, and
an overall translation. Placing `{#ex:...}` after the translation line
introduces a new label, which can then be referred to with the `@ex:...`
syntax as in [pandoc-crossref](https://github.com/lierdakil/pandoc-crossref).
Similar customization of labels and more advanced references are coming soon.

### Changes from [the original repo](https://github.com/daemanos/pangloss)

As noted in [an issue](https://github.com/daemanos/pangloss/issues/8), 
`pangloss` does not coexist with [pandoc's Numbered example lists](https://pandoc.org/MANUAL.html#numbered-example-lists).
That is, with `pangloss`, pandoc's Numbered example lists notation `(@)` is always ignored and the list disappears in the final output.

This is undesirable because we cannot include some examples without any interlinear morpheme-by-morpheme glosses and translation
(e.g. we cannot add gloss-less examples by using `(@)` notation).

At this time, `pangloss` still overrides the notation of pandoc's Numbered example lists.
However, backend.py is updated and in the file the automated insertion of the single quotation marks into the translation line (3rd line of an expample) is disabled so that unwanted single quotation marks disappears when an example does not require any interlinear morpheme-by-morpheme glosses (2nd line) and translation (3rd line). 
In other words, we can include gloss-less examples via `pangloss` by adding "null" characters such as `{}` to the 2nd and 3rd line.

## Installation

Install with:

```bash
git clone https://github.com/CLRafaelR/pangloss pangloss
```

Use with:

```bash
pandoc in.md -F pangloss -o out.{pdf,html}
```
