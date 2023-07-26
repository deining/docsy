---
title: "PGF/TikZ: Drawings for LaTeX"
linkTitle: "TikZ (drawings for LaTeX)"
date: 2023-03-31T21:13:54+02:00
draft: false
math: true
weight: 173
description: >
  Author graphics using the TikZ frontend and the underlying [PGF](https://github.com/pgf-tikz/pgf) TeX macro package.
---
## Overview and example drawings

[PGF/TikZ](https://en.wikipedia.org/wiki/PGF/TikZ) allows you to author sophisticated technical diagrams using the [PGF](https://github.com/pgf-tikz/pgf) \\(\TeX\\) macro package. [TikZ](https://tikz.de) is user-friendly syntax layer around lower-level PGF macro package. See the [user manual](https://pgf-tikz.github.io) for details on how to author your diagrams. You may find the [example gallery](https://texample.net/tikz/examples/) useful, too. There is also a [demonstration](http://www.math.tugraz.at/~huss/new/teaching/computermathematik09/dateien/tikz_demonstration.pdf) available that shows many small, but several small code samples.

## Embedding your TikZ drawing

### Drawing source embedded in code block

To embed a `TikZ` drawing in your page, use a `tikz` code block and put the drawing source in the body of the block. An example is given below, rendering a drawing of the [Penrose triangle](https://en.wikipedia.org/wiki/Penrose_triangle) as output:

````
```tikz
\documentclass{standalone}
\usepackage{tikz}
\begin{document}
  \begin{tikzpicture}[scale=1, line join=bevel]
    \pgfmathsetmacro{\a}{2.5}
    \pgfmathsetmacro{\b}{0.9}
    \tikzset{%
      apply style/.code     = {\tikzset{#1}},
      triangle_edges/.style = {thick,draw=black}
    }
    \foreach \theta/\facestyle in {%
        0/{triangle_edges, fill = gray!50},
      120/{triangle_edges, fill = gray!25},
      240/{triangle_edges, fill = gray!90}%
    }{
      \begin{scope}[rotate=\theta]
        \draw[apply style/.expand once=\facestyle]
          ({-sqrt(3)/2*\a},{-0.5*\a})                     --
          ++(-\b,0)                                       --
            ({0.5*\b},{\a+3*sqrt(3)/2*\b})                -- % higher point
            ({sqrt(3)/2*\a+2.5*\b},{-.5*\a-sqrt(3)/2*\b}) -- % rightmost point
          ++({-.5*\b},-{sqrt(3)/2*\b})                    -- % lower point
            ({0.5*\b},{\a+sqrt(3)/2*\b})                  --
          cycle;
      \end{scope}
    }
  \end{tikzpicture}
\end{document}
```
````

The code block above renders to this drawing:

```tikz
% Author: Julien Cretel
% Date:   24/02/2013
\documentclass{standalone}
\usepackage{tikz}
\begin{document}
    \begin{tikzpicture}[scale=1, line join=bevel]
    % \a and \b are two macros defining characteristic
    % dimensions of the Penrose triangle.		
    \pgfmathsetmacro{\a}{2.5}
    \pgfmathsetmacro{\b}{0.9}
    \tikzset{%
      apply style/.code     = {\tikzset{#1}},
      triangle_edges/.style = {thick,draw=black}
    }
    \foreach \theta/\facestyle in {%
        0/{triangle_edges, fill = gray!50},
      120/{triangle_edges, fill = gray!25},
      240/{triangle_edges, fill = gray!90}%
    }{
      \begin{scope}[rotate=\theta]
        \draw[apply style/.expand once=\facestyle]
          ({-sqrt(3)/2*\a},{-0.5*\a})                     --
          ++(-\b,0)                                       --
            ({0.5*\b},{\a+3*sqrt(3)/2*\b})                -- % higher point	
            ({sqrt(3)/2*\a+2.5*\b},{-.5*\a-sqrt(3)/2*\b}) -- % rightmost point
          ++({-.5*\b},-{sqrt(3)/2*\b})                    -- % lower point
            ({0.5*\b},{\a+sqrt(3)/2*\b})                  --
          cycle;
        \end{scope}diag
    }	
  \end{tikzpicture}
\end{document}
```

### Reading drawing source from file

For more complex TikZ drawings, there is the option to read the drawing source from a file. To do so, pass the parameter `sourcefile` as attribute of the code block:

````
```tikz { sourcefile="penrose-triangle.diag" }
```
````

Using this [source file](penrose-triangle.diag), the same Penrose triangle as above is shown.

{{%alert title="Note" color="primary" %}}
The source file needs to be a [page resource](https://gohugo.io/content-management/page-resources/) bundled to the page containing the TikZ drawing.
{{%/alert%}}

## Supported output formats

The default output format is `svg`. By using the `format` option (see below), you can opt for `png`, `jpeg` or `pdf` as output format, too. 

## Drawing options

Your drawing can be customized using the options listed below: 

| Option name     | Allowable values                                  | Description                                 |
|-----------------|---------------------------------------------------|---------------------------------------------|
| sourcefile      | string                                            | Name of file containing drawing source code |
| format          | _svg_, _png_, _jpeg_ or _pdf_                     | Output format of generated drawing          |
| disabled        | boolean,<br>_true_ or _false_                     | Disable/skip drawing                        |

If you want to make use of these option(s), you have to give them as attributes to your `tikz` code block, as shown in the listing below:

````
```tikz {format="svg" disabled=false }
drawing source goes here
```
````
