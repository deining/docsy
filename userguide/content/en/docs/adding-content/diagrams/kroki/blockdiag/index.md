---
title: "Block diagrams (blockdiag)"
linkTitle: "Block diagrams"
date: 2023-03-14T21:37:56+01:00
draft: false
weight: 20
description: >
  Author block diagrams using the [blockdiag](http://blockdiag.com/en/blockdiag/) library.
---
## Overview and example diagrams

The [blockdiag library](https://github.com/blockdiag/blockdiag) allows you do generate block diagrams via a textual description of the blocks to be depicted. Use the [documentation](http://blockdiag.com/en/blockdiag/) for syntax details.
Also, you may find these [example diagrams](https://github.com/blockdiag/blockdiag/tree/master/examples) useful, too.


## Authoring your block diagram

### Diagram source embedded in code block

To embed a block diagram in your page, use a `blockdiag` code block and put the diagram source in the body of the block. An example is given below: 

````
```blockdiag
{
  Docsy -> supports -> "block diagrams";
  Docsy -> is -> "awesome!";

  Docsy [color = "greenyellow"];
  "block diagrams" [color = "pink"];
  "awesome!" [color = "orange"];
}
```
````

The code block above renders to this block diagram:

```blockdiag
{
  Docsy -> supports -> "block diagrams";
  Docsy -> is -> "awesome!";

  Docsy [color = "greenyellow"];
  "block diagrams" [color = "pink"];
  "awesome!" [color = "orange"];
}
```

### Reading diagram source from file

For more complex block diagrams, there is the option to read the diagram source from a file. To do so, pass the parameter `sourcefile` as attribute of the code block:

````
```blockdiag { sourcefile="block-simple.diag" }
```
````

Using this [source file](block-simple.diag), the same diagram as above is shown.

## Supported output formats

The default output format is `svg`. By using the `format` option (see below), you can opt for `png` or `pdf` as output format, too. 

## Diagram options

Your diagram can be customized using the options listed below: 

| Option name     | Allowable values                                  | Description                                  |
|-----------------|---------------------------------------------------|----------------------------------------------|
| sourcefile      | string                                            | Name of file containing diagram source code  |
| format          | _svg_, _png_ or _pdf_                             | Output format of generated diagram image     |
| disabled        | boolean,<br>_true_ or _false_                     | Disable/skip diagram                         |
| antialias       | flag,<br>empty string ("")                        | Pass diagram image to anti-alias filter      |
| no-transparency | flag,<br>empty string ("")                        | No transparent diagram background (PNG only) |
| size            | dimensions,<br>_width_x_height_<br>e.g. _320x240_ | Size of diagram                              |
| no-doctype      | flag,<br>empty string ("")                        | Omit doctype definition tags (SVG only)      |

If you want to make use of these option(s), you have to give them as attributes to your `blockdiag` code block, as shown in the listing below:

````
```blockdiag {format="svg" disabled=false antialias="" no-transparency="" size="30x30" no-doctype="" }
diagram source goes here
```
````

Alternatively, when reading the diagram source from a file, the parameters can be given inside the code block, too. Use the json format for notation inside the body of your block:

````
```blockdiag { sourcefile="block-simple.diag" format="svg" disabled=false antialias="" no-transparency="" size="30x30" no-doctype="" }
{
  "format": "svg",
  "disabled": "false",
  "antialias": "",
  "no-transparency": "",
  "size": "30x30"
}
```
````
