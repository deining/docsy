---
title: Formulae
linkTitle: Formulae
weight: 11
description: Add scientific formulae to your site.
math: true
chem: true
---

Docsy has built-in support for a number of diagram creation and typesetting tools you can use to add rich content to your site, including \\(\KaTeX\\), Mermaid, Diagrams.net, PlantUML, and MarkMap.

## \\(\LaTeX\\) support with \\(\KaTeX\\)

[\\(\LaTeX\\)](https://www.latex-project.org/) is a high-quality typesetting system for the production of technical and scientific documentation. Due to its excellent math typesetting capabilities, \\(\TeX\\) became the de facto standard for the communication and publication of scientific documents, especially if these documents contain a lot of mathematical formulae. Designed and mostly written by Donald Knuth, the initial version was released in 1978. Dating back that far, \\(\LaTeX\\) has `pdf` as its primary output target and is not particularly well suited for producing HTML output for the Web. Fortunately, with [\\(\KaTeX\\)](https://katex.org/) there exists a fast and easy-to-use JavaScript library for \\(\TeX\\) math rendering on the web, which was integrated into the Docsy theme.

With \\(\KaTeX\\) support [enabled](#activating-and-configuring-katex-support) in Docsy, you can include complex mathematical formulae into your web page, either inline or centred on its own line. Since \\(\KaTeX\\) relies on server side rendering, it produces the same output regardless of your browser or your environment. Formulae can be shown either inline or in display mode:

### Inline formulae

The following code sample produces a text line with three inline formulae:

```tex
When \\(a \ne 0\\), there are two solutions to \\(ax^2 + bx + c= 0\\) and they are \\(x = {-b \pm \sqrt{b^2-4ac} \over 2a}\\).
```

When \\(a \ne 0\\), there are two solutions to \\(ax^2 + bx + c= 0\\) and they are \\(x = {-b \pm \sqrt{b^2-4ac} \over 2a}\\).

### Formulae in display mode

The following code sample produces an introductory text line followed by a formula numbered as `(1)` residing on its own line:

````markdown
The probability of getting \\(k\\) heads when flipping \\(n\\) coins is:
```math
\tag*{(1)} P(E) = {n \choose k} p^k (1-p)^{n-k}
```
````

The formula itself is written inside a [GLFM math block](https://docs.gitlab.com/ee/user/markdown.html#math). The above code fragment renders to:

The probability of getting \\(k\\) heads when flipping \\(n\\) coins is:
```math
\tag*{(1)}  P(E) = {n \choose k} p^k (1-p)^{n-k}
```

{{% alert title="Warning" color="warning" %}}
`math` code blocks are only supported as of hugo version 0.93.

In case of hugo version 0.92 or lower, use this code snippet to display the formula:
```tex
$$
\tag*{(1)} P(E) = {n \choose k} p^k (1-p)^{n-k}
$$
```
{{% /alert %}}

{{% alert title="Tip" %}}
This [wiki page](https://en.wikibooks.org/wiki/LaTeX/Mathematics) provides in-depth information about typesetting mathematical formulae using the \\(\LaTeX\\) typesetting system.
{{% /alert %}}

### Activating and configuring \\(\KaTeX\\) support

#### Auto activation

As soon as you use a `math` code block on your page, support of \\(\KaTeX\\) is automatically enabled.

#### Manual activation (no `math` code block present or hugo 0.92 or lower)

If you want to use inline formulae and don't have a `math` code block present in your page which triggers auto activation, you need to manually activate \\(\KaTeX\\) support. The easiest way to do so is to add a `math` attribute to the frontmatter of your page and set it to `true`:

{{< tabpane >}}
{{< tab header="Page front matter:" disabled=true />}}
{{< tab header="toml" lang="toml" >}}
+++
math = true
+++
{{< /tab >}}
{{< tab header="yaml" lang="yaml" >}}
---
math: true
---
{{< /tab >}}
{{< tab header="json" lang="json" >}}
{
  "math": true
}
{{< /tab >}}
{{< /tabpane >}}

If you use formulae in most of your pages, you can also enable sitewide \\(\KaTeX\\) support inside the Docsy theme. To do so update `hugo.toml`/`hugo.yaml`/`hugo.json`:

{{< tabpane >}}
{{< tab header="Site configuration file:" disabled=true />}}
{{< tab header="hugo.toml" lang="toml" >}}
[params.katex]
enable = true
{{< /tab >}}
{{< tab header="hugo.yaml" lang="yaml" >}}
params:
  katex:
    enable: true
{{< /tab >}}
{{< tab header="hugo.json" lang="json" >}}
{
  "params": {
    "katex": {
      "enable": true
    }
  }
}
{{< /tab >}}
{{< /tabpane >}}

Additionally, you can customize various \\(\KaTeX\\) options inside `hugo.toml`/`hugo.yaml`/`hugo.json`, if needed:

{{< tabpane >}}
{{< tab header="Site configuration file:" disabled=true />}}
{{< tab header="hugo.toml" lang="toml" >}}
[params.katex]
# enable/disable KaTeX support
enable = true
# Element(s) scanned by auto render extension. Default: document.body
html_dom_element = "document.body"

[params.katex.options]
# If true (the default), KaTeX will throw a ParseError when it encounters an
# unsupported command or invalid LaTeX. If false, KaTeX will render unsupported
# commands as text, and render invalid LaTeX as its source code with hover text
# giving the error, in the color given by errorColor.
throwOnError = false
errorColor = "#CD5C5C"

# This is a list of delimiters to look for math, processed in the same order as
# the list. Each delimiter has three properties:
#   left:    A string which starts the math expression (i.e. the left delimiter).
#   right:   A string which ends the math expression (i.e. the right delimiter).
#   display: Whether math in the expression should be rendered in display mode.
[[params.katex.options.delimiters]]
  left = "$$"
  right = "$$"
  display = true
[[params.katex.options.delimiters]]
  left = "$"
  right = "$"
  display = false
[[params.katex.options.delimiters]]
  left = "\\("
  right = "\\)"
  display = false
[[params.katex.options.delimiters]]
  left = "\\["
  right = "\\]"
  display = true
{{< /tab >}}
{{< tab header="hugo.yaml" lang="yaml" >}}
params:
  katex:
    enable: true  # enable/disable KaTeX support
    html_dom_element: document.body  # Element(s) scanned by auto render extension. Default: document.body
    options:

      # If true (the default), KaTeX will throw a ParseError when it encounters an
      # unsupported command or invalid LaTeX. If false, KaTeX will render unsupported
      # commands as text, and render invalid LaTeX as its source code with hover text
      # giving the error, in the color given by errorColor.
      throwOnError: false
      errorColor: '#CD5C5C'

      # This is a list of delimiters to look for math, processed in the same order as
      # the list. Each delimiter has three properties:
      #   left:    A string which starts the math expression (i.e. the left delimiter).
      #   right:   A string which ends the math expression (i.e. the right delimiter).
      #   display: Whether math in the expression should be rendered in display mode.
      delimiters:
        - left: $$
          right: $$
          display: true
        - left: $
          right: $
          display: false
        - left: \(
          right: \)
          display: false
        - left: \[
          right: \]
          display: true
{{< /tab >}}
{{< tab header="hugo.json" lang="json" >}}
{
  "params": {
    "katex": {
      "enable": true,
      "html_dom_element": "document.body",
      "options": {
        "throwOnError": false,
        "errorColor": "#CD5C5C",
        "delimiters": [
          {
            "left": "$$",
            "right": "$$",
            "display": true
          },
          {
            "left": "$",
            "right": "$",
            "display": false
          },
          {
            "left": "\\(",
            "right": "\\)",
            "display": false
          },
          {
            "left": "\\[",
            "right": "\\]",
            "display": true
          }
        ]
      }
    }
  }
}
{{< /tab >}}
{{< /tabpane >}}

For a complete list of options and their detailed description, have a look at the documentation of \\({\KaTeX}'s\\) [Rendering API options](https://katex.org/docs/autorender.html#api) and of \\({\KaTeX}'s\\) [configuration options](https://katex.org/docs/options.html).

### Display of Chemical Equations and Physical Units

[mhchem](https://www.ctan.org/pkg/mhchem) is a \\(\LaTeX\\) package for typesetting chemical molecular formulae and equations. Fortunately, \\(\KaTeX\\) provides the `mhchem` [extension](https://github.com/KaTeX/KaTeX/tree/main/contrib/mhchem) that makes the `mhchem` package accessible when authoring content for the web. With `mhchem` extension [enabled](#activating-rendering-support-for-chemical-formulae), you can easily include chemical equations into your page. An equation can be shown either inline or can reside on its own line. The following code sample produces a text line including a chemical equation:

```mhchem
*Precipitation of barium sulfate:* \\(\ce{SO4^2- + Ba^2+ -> BaSO4 v}\\)
```

*Precipitation of barium sulfate:* \\(\ce{SO4^2- + Ba^2+ -> BaSO4 v}\\)

More complex equations need to be displayed on their own line. Use a code block adorned with `chem` in order to achieve this:

````markdown
```chem
\tag*{(2)} \ce{Zn^2+  <=>[+ 2OH-][+ 2H+]  $\underset{\text{amphoteric hydroxide}}{\ce{Zn(OH)2 v}}$  <=>[+ 2OH-][+ 2H+]  $\underset{\text{tetrahydroxozincate}}{\ce{[Zn(OH)4]^2-}}$}
```
````

```chem
\tag*{(2)} \ce{Zn^2+  <=>[+ 2OH-][+ 2H+]  $\underset{\text{amphoteric hydroxide}}{\ce{Zn(OH)2 v}}$  <=>[+ 2OH-][+ 2H+]  $\underset{\text{tetrahydroxozincate}}{\ce{[Zn(OH)4]^2-}}$}
```

{{% alert title="Warning" color="warning" %}}
`chem` code blocks are only supported as of hugo version 0.93.

In case of hugo version 0.92 or lower, use this code snippet to display the formula:
```tex
$$
\tag*{(2)} \ce{Zn^2+  <=>[+ 2OH-][+ 2H+]  $\underset{\text{amphoteric hydroxide}}{\ce{Zn(OH)2 v}}$  <=>[+ 2OH-][+ 2H+]  $\underset{\text{tetrahydroxozincate}}{\ce{[Zn(OH)4]^2-}}$}
$$
```
{{% /alert %}}

{{% alert title="Note" %}}
The [manual](https://mhchem.github.io/MathJax-mhchem/) for mchem’s input syntax provides in-depth information about typesetting chemical formulae and physical units using the `mhchem` tool.
{{% /alert %}}

Use of `mhchem` is not limited to the authoring of chemical equations, using the included `\pu` command, pretty looking physical units can be written with ease, too. The following code sample produces two text lines with four numbers plus their corresponding physical units:

```mhchem
* Scientific number notation: \\(\pu{1.2e3 kJ}\\) or \\(\pu{1.2E3 kJ}\\) \\
* Divisions: \\(\pu{123 kJ/mol}\\) or \\(\pu{123 kJ//mol}\\)
```

* Scientific number notation: \\(\pu{1.2e3 kJ}\\) or \\(\pu{1.2E3 kJ}\\)
* Divisions: \\(\pu{123 kJ/mol}\\) or \\(\pu{123 kJ//mol}\\)

For a complete list of options when authoring physical units, have a look at the [section](https://mhchem.github.io/MathJax-mhchem/#pu) on physical units in the `mhchem` documentation.

#### Activating rendering support for chemical formulae

##### Auto activation

As soon as you use a `chem` code block on your page, rendering support for chemical equations is automatically enabled.

##### Manual activation (no `chem` code block present or hugo 0.92 or lower)

If you want to use chemical formulae inline and don't have a `chem` code block present in your page which triggers auto activation, you need to manually activate rendering support for chemical formulae. The easiest way to do so is to add a `chem` attribute to the frontmatter of your page and set it to `true`:

{{< tabpane >}}
{{< tab header="Page front matter:" disabled=true />}}
{{< tab header="toml" lang="toml" >}}
+++
chem = true
+++
{{< /tab >}}
{{< tab header="yaml" lang="yaml" >}}
---
chem: true
---
{{< /tab >}}
{{< tab header="json" lang="json" >}}
{
  "chem": true
}
{{< /tab >}}
{{< /tabpane >}}

If you use formulae in most of your pages, you can also enable sitewide rendering support for chemical formulae inside the Docsy theme. To do so, enable `mhchem` inside your `hugo.toml`/`hugo.yaml`/`hugo.json`:

{{< tabpane >}}
{{< tab header="Site configuration file:" disabled=true />}}
{{< tab header="hugo.toml" lang="toml" >}}
[params.katex]
enable = true

[params.katex.mhchem]
enable = true
{{< /tab >}}
{{< tab header="hugo.yaml" lang="yaml" >}}
params:
  katex:
    enable: true
    mhchem:
      enable: true
{{< /tab >}}
{{< tab header="hugo.json" lang="json" >}}
{
  "params": {
    "katex": {
      "enable": true,
      "mhchem": {
        "enable": true
      }
    }
  }
}
{{< /tab >}}
{{< /tabpane >}}
