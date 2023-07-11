---
title: "Diagrams Through ASCII Art (ditaa)"
linkTitle: "Diagrams Through ASCII Art"
date: 2023-03-14T21:40:18+01:00
draft: false
weight: 48
description: >
  Author diagrams through ASCII art, using the [ditaa](https://ditaa.sourceforge.net/) command line tool.
---

## Overview

The [ditaa](https://ditaa.sourceforge.net/) command line utility allows you do generate diagrams from ASCII art. Consult the [Usage](https://ditaa.sourceforge.net/#usage) section of the `ditaa` homepage  for syntax details.

## Authoring your ASCII art diagram

### Diagram source embedded in code block

To embed an ASCII art diagram in your page, use a `ditaa` code block and put the diagram source in the body of the block. An example is given below:

````
```ditaa
+-----------+  +------+   +---------------+
| cGRE      |  | cBLK |   | cYEL          |
| Markdown  |--+ hugo +-->| great looking |
| documents |  |      |   | documentation |
|        {d}|  +------+   |   website     |
+-----+-----+      +      |               |
      :        +-------+  +---------------+
      |        | cBLU  |          ^
      |        | docsy |          |
      |        | theme |          |
      |        |       |          |
      |        +++++++++          |
      |                           |
      |  Lots of authoring work   |
      +---------------------------+
```
````

The code block above renders to this ASCII art diagram:

```ditaa
+-----------+  +------+   +---------------+
| cGRE      |  | cBLK |   | cYEL          |
| Markdown  |--+ hugo +-->| great looking |
| documents |  |      |   | documentation |
|        {d}|  +------+   |   website     |
+-----+-----+      +      |               |
      :        +-------+  +---------------+
      |        | cBLU  |          ^
      |        | docsy |          |
      |        | theme |          |
      |        |       |          |
      |        +++++++++          |
      |                           |
      |  Lots of authoring work   |
      +---------------------------+
```

### Reading diagram source from file

For more complex ASCII art diagrams, there is the option to read the diagram source from a file. To do so, pass the parameter `sourcefile` as attribute of the code block:

````
```ditaa { sourcefile="ditaa-simple.diag" }
```
````

Using this [source file](ditaa-simple.diag), the same diagram as above is shown.

## Supported output formats

The default output format is `svg`. By using the `format` option (see below), you can opt for `png` or `pdf` as output format, too. 

## Diagram options

Your diagram can be customized using the options listed below: 

| Option name     | Allowable values                                  | Description                                  |
|-----------------|---------------------------------------------------|----------------------------------------------|
| sourcefile      | string                                            | Name of file containing diagram source code  |
| format          | _svg_ or _png_                                    | Output format of generated diagram image     |
| disabled        | boolean,<br>_true_ or _false_                     | Disable/skip diagram                         |

If you want to make use of these option(s), you have to give them as attributes to your `ditaa` code block, as shown in the listing below:

````
```ditaa { format="png" disabled=false }
diagram source goes here
```
````
