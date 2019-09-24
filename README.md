# remark-music

[**remark**][remark] plugin to parse and stringify music.

## Install

```sh
npm install remark-music
```

## Use

Just wrap your abc string into double section signs (§)

e.g.

```markdown
§§
X: 24
T:Clouds Thicken
C:Paul Rosen
S:Copyright 2005, Paul Rosen
M:6/8
L:1/8
Q:3/8=116
R:Creepy Jig
K:Em
|:"Em"EEE E2G|"C7"_B2A G2F|"Em"EEE E2G|\
"C7"_B2A "B7"=B3|"Em"EEE E2G|
"C7"_B2A G2F|"Em"GFE "D (Bm7)"F2D|\
1"Em"E3-E3:|2"Em"E3-E2B|:"Em"e2e gfe|
"G"g2ab3|"Em"gfeg2e|"D"fedB2A|"Em"e2e gfe|\
"G"g2ab3|"Em"gfe"D"f2d|"Em"e3-e3:|
§§
```

<!-- TODO
Say we have the following file, `example.md`:

```markdown
Lift(§L§) can be determined by Lift Coefficient (§C_L§) like the following equation.

§§
L = \frac{1}{2} \rho v^2 S C_L
§§
```

And our script, `example.js`, looks as follows:

```js
const vfile = require('to-vfile')
const unified = require('unified')
const markdown = require('remark-parse')
const music = require('remark-music')
const remark2rehype = require('remark-rehype')
const katex = require('rehype-katex')
const stringify = require('rehype-stringify')

unified()
  .use(markdown)
  .use(music)
  .use(remark2rehype)
  .use(katex)
  .use(stringify)
  .process(vfile.readSync('example.md'), function(err, file) {
    if (err) throw err
    console.log(String(file))
  })
```

Now, running `node example` yields:

```html
```
-->

## API

### `remark().use(music[, options])`

Parse and stringify music.

Get’s useful when combined with [`rehype-katex`][rehype-katex] or
[`remark-html-katex`][remark-html-katex].

#### `options`

See [abcjs](https://github.com/paulrosen/abcjs) options.

#### Notes

##### Escaping

You can escape section signs with a back slash (`\`):

```markdown
\§\alpha\§

§\alpha\§§

§§
\beta\§
§§
```

## Security

Use of `remark-music` itself doesn’t open you up to [cross-site scripting XSS attacks.

Always be wary of user input and use `rehype-sanitize`.

## License

MIT
