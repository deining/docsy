---
title: "Pikchr diagrams (technical documentation)"
linkTitle: "Pikchr diagrams"
date: 2023-03-14T21:41:38+01:00
draft: false
weight: 130
description: >
  Author diagrams in technical documentation using the [PIC](https://en.wikipedia.org/wiki/PIC_(markup_language)) like markup language.
---
## Overview and example diagrams

[Pikchr](https://pikchr.org) (pronounced `picture`) allows you to author sophisticated technical diagrams in a [PIC](https://en.wikipedia.org/wiki/PIC_(markup_language)) like [markup language](https://pikchr.org/home/doc/trunk/doc/grammar.md). See the [user manual](https://pikchr.org/home/doc/trunk/doc/userman.md) for details on how to author your diagrams.
You may find these [example diagrams](https://pikchr.org/home/doc/trunk/doc/examples.md) useful, too.

## Authoring your technical diagram

### Diagram source embedded in code block

To embed a `Pikchr` technical diagram in your page, use a `pikchr` code block and put the diagram source in the body of the block. An example is given below, producing a drawing of the [impossible trident](https://en.wikipedia.org/wiki/Impossible_trident) as output:

````
```pikchr
scale = 1.0
eh = 0.5cm
ew = 0.2cm
ed = 2 * eh
er = 0.4cm
lws = 4.0cm
lwm = lws + er
lwl = lwm + er

ellipse height eh width ew
L1: line width lwl from last ellipse.n
line width lwm from last ellipse.s
LV: line height eh down

move right er down ed from last ellipse.n
ellipse height eh width ew
L3: line width lws right from last ellipse.n to LV.end then down eh right ew
line width lwm right from last ellipse.s then to LV.start

move right er down ed from last ellipse.n
ellipse height eh width ew
line width lwl right from last ellipse.n then to L1.end
line width lwl right from last ellipse.s then up eh
```
````

The code block above renders to a drawing of the [impossible trident](https://en.wikipedia.org/wiki/Impossible_trident):

```pikchr
# Impossible trident pikchr script
# https://en.wikipedia.org/wiki/Impossible_trident
# pikchr script by Kees Nuyt, license Creative Commons BY-NC-SA 
# https://creativecommons.org/licenses/by-nc-sa/4.0/

scale = 1.5
eh = 0.5cm
ew = 0.2cm
ed = 2 * eh
er = 0.4cm
lws = 4.0cm
lwm = lws + er
lwl = lwm + er

ellipse height eh width ew
L1: line width lwl from last ellipse.n
line width lwm from last ellipse.s
LV: line height eh down

move right er down ed from last ellipse.n
ellipse height eh width ew
L3: line width lws right from last ellipse.n to LV.end then down eh right ew
line width lwm right from last ellipse.s then to LV.start

move right er down ed from last ellipse.n
ellipse height eh width ew
line width lwl right from last ellipse.n then to L1.end
line width lwl right from last ellipse.s then up eh
```

### Reading diagram source from file

For more complex Pikchr diagrams, there is the option to read the diagram source from a file. To do so, pass the parameter `sourcefile` as attribute of the code block:

````
```pikchr { sourcefile="impossible-trident.diag" }
```
````

Using this [source file](impossible-trident.diag), the same impossible trident as above is shown.

{{%alert title="Note" color="primary" %}}
The source file needs to be a [page resource](https://gohugo.io/content-management/page-resources/) bundled to the page containing the Pikchr diagram.
{{%/alert%}}

## Supported output formats

The only supported output format is `svg`.

## Diagram options

Your diagram can be customized using the options listed below: 

| Option name     | Allowable values                                  | Description                                  |
|-----------------|---------------------------------------------------|----------------------------------------------|
| sourcefile      | string                                            | Name of file containing diagram source code  |
| disabled        | boolean,<br>_true_ or _false_                     | Disable/skip diagram                         |

If you want to make use of these option(s), you have to give them as attributes to your `pikchr` code block, as shown in the listing below:

````
```pikchr { disabled=false }
diagram source goes here
```
````
