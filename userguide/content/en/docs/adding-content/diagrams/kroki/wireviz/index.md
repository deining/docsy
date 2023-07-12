---
title: "Wiring diagrams (WireViz)"
linkTitle: "Wiring diagrams"
date: 2023-03-14T21:34:22+01:00
draft: false
weight: 200
description: >
  Author wiring diagrams using the [WireViz](https://github.com/wireviz/WireViz) tool.
---
## Overview and example diagrams

The [WireViz](https://github.com/wireviz/WireViz) tool creates wiring diagram from a textual description of the wiring to be depicted. The tool is meant for documenting cables, wiring harnesses and connector pinouts. Visit the [tutorial page](http://blockdiag.com/en/actdiag/) for code samples.
You also might want to have a look at the [example diagrams](https://github.com/wireviz/WireViz/blob/master/examples/readme.md).

## Authoring your wiring diagram

### Diagram source embedded in code block

To embed an wiring diagram in your page, use a `wireviz` code block and put the diagram source in the body of the block. An example is given below:

````
```wireviz { format="svg"}
connectors:
connectors:
  X1:
    pincount: 2
  X2:
    pincount: 2

cables:
  W1:
    wirecount: 2
    length: 1
    colors: [BK, BU]

connections:
  -
    - X1: [1-2]
    - W1: [1-2]
    - X2: [1-2]
```
````

The code block above renders to this wiring diagram:

```wireviz { format="svg"}
connectors:
connectors:
  X1:
    pincount: 2
  X2:
    pincount: 2

cables:
  W1:
    wirecount: 2
    length: 1
    colors: [BK, BU]

connections:
  -
    - X1: [1-2]
    - W1: [1-2]
    - X2: [1-2]
```

### Reading diagram source from file

For more complex wiring diagrams, there is the option to read the diagram source from a file. To do so, pass the parameter `sourcefile` as attribute of the code block:

````
```wireviz { sourcefile="wiring-simple.diag" }
```
````

Using this [source file](wiring-simple.diag), the same diagram as above is shown.

## Supported output formats

The only  output format for wiring diagrams is `svg`.

## Diagram options

Your diagram can be customized using the options listed below: 

| Option name     | Allowable values                                  | Description                                  |
|-----------------|---------------------------------------------------|----------------------------------------------|
| sourcefile      | string                                            | Name of file containing diagram source code  |
| disabled        | boolean,<br>_true_ or _false_                     | Disable/skip diagram                         |

If you want to make use of these option(s), you have to give them as attributes to your `wireviz` code block, as shown in the listing below:

````
```wireviz { sourcefile="wiring-simple.diag" disabled=false }
diagram source goes here
```
````
