---
title: "Mindmap diagrams with Markmap"
linkTitle: "Mindmap diagrams"
date: 2023-04-13T12:28:47+02:00
draft: false
weight: 30
description: >
  Author mindmap diagrams, using the [markmap](https://markmap.js.org/) library.
---
[MarkMap](https://markmap.js.org/) is a Javascript library for rendering simple text definitions to MindMap in the browser.

For example, the following defines a simple MindMap:

````
```markmap
# markmap

## Links

- <https://markmap.js.org/>
- [GitHub](https://github.com/gera2ld/markmap)

## Related

- [coc-markmap](https://github.com/gera2ld/coc-markmap)
- [gatsby-remark-markmap](https://github.com/gera2ld/gatsby-remark-markmap)

## Features

- links
- **inline** ~~text~~ *styles*
- multiline
  text
- `inline code`
-
    ```js
    console.log('code block');
    ```
- Katex - $x = {-b \pm \sqrt{b^2-4ac} \over 2a}$
```
````

Automatically renders to:

```markmap
# markmap

## Links

- <https://markmap.js.org/>
- [GitHub](https://github.com/gera2ld/markmap)

## Related

- [coc-markmap](https://github.com/gera2ld/coc-markmap)
- [gatsby-remark-markmap](https://github.com/gera2ld/gatsby-remark-markmap)

## Features

- links
- **inline** ~~text~~ *styles*
- multiline
  text
- `inline code`
-
    ```js
    console.log('code block');
    ```
- Katex - $x = {-b \pm \sqrt{b^2-4ac} \over 2a}$
```

To enable/disable MarkMap, update `hugo.toml`/`hugo.yaml`/`hugo.json`:

{{< tabpane >}}
{{< tab header="Configuration file:" disabled=true />}}
{{< tab header="hugo.toml" lang="toml" >}}
[params.markmap]
enable = true
{{< /tab >}}
{{< tab header="hugo.yaml" lang="yaml" >}}
params:
  markmap:
    enable: true
{{< /tab >}}
{{< tab header="hugo.json" lang="json" >}}
{
  "params": {
    "markmap": {
      "enable": true
    }
  }
}
{{< /tab >}}
{{< /tabpane >}}
