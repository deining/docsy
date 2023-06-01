---
title: "Rack diagrams (rackdiag)"
linkTitle: "Rack diagrams"
date: 2023-03-14T21:39:26+01:00
draft: false
weight: 150
description: >
  Author rack diagrams using the [nwdiag](http://blockdiag.com/en/nwdiag/) library.
---
## Overview and example diagrams

The [nwdiag library](https://github.com/blockdiag/nwdiag/tree/master/src/packetdiag) allows you do generate rack diagrams via a textual description of the rack to be depicted. Use the [documentation](http://blockdiag.com/en/nwdiag/rackdiag-examples.html) for syntax details.

## Authoring your rack diagram

### Diagram source embedded in code block

To embed a rack diagram in your page, use a `rackdiag` code block and put the diagram source in the body of the block.  An example is given below:

````
```rackdiag
{
  16U;
  1: UPS [2U];
  3: DB Server;
  4: Web Server;
  5: Web Server;
  6: Web Server;
  7: Load Balancer;
  8: L3 Switch;
}
```
````

The code block above renders to this rack diagram:

```rackdiag
{
  16U;
  1: UPS [2U];
  3: DB Server;
  4: Web Server;
  5: Web Server;
  6: Web Server;
  7: Load Balancer;
  8: L3 Switch;
}
```

### Reading diagram source from file

For more complex rack diagrams, there is the option to read the diagram source from a file. To do so, pass the parameter `sourcefile` as attribute of the code block:

````
```rackdiag { sourcefile="rack-simple.diag" }
```
````

Using this [source file](rack-simple.diag), the same diagram as above is shown.

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

If you want to make use of these option(s), you have to give them as attributes to your `rackdiag` code block, as shown in the listing below:

````
```rackdiag {format="svg" disabled=false antialias="" no-transparency="" size="30x30" no-doctype="" }
diagram source goes here
```
````

Alternatively, when reading the diagram source from a file, the parameters can be given inside the code block, too. Use the json format for notation inside the body of your block:

````
```rackdiag { sourcefile="rack-simple.diag" format="svg" disabled=false antialias="" no-transparency="" size="30x30" no-doctype="" }
{
  "format": "svg",
  "disabled": "false",
  "antialias": "",
  "no-transparency": "",
  "size": "30x30"
}
```
````