---
title: "Network diagrams (nwdiag)"
linkTitle: "Network diagrams"
date: 2023-03-14T21:34:22+01:00
draft: false
weight: 110
description: >
  Author network diagrams using the `packetdiag` script from the [nwdiag](http://blockdiag.com/en/nwdiag/) library.
---
## Overview and example diagrams

The [nwdiag library](https://github.com/blockdiag/nwdiag) allows you to generate network diagrams via a textual description of the network to be depicted. Use the [documentation](http://blockdiag.com/en/nwdiag/) for syntax details.
You may find these [example diagrams](https://github.com/blockdiag/nwdiag/tree/master/examples/nwdiag) useful, too.

## Authoring your network diagram

### Diagram source embedded in code block

To embed a network diagram in your page, use a `nwdiag` code block and put the diagram source in the body of the block. An example is given below: 

````
```nwdiag
{
  network dmz {
      address = "10.10.x.x/16"

      web01 [address = "10.10.x.1"];
      web02 [address = "10.10.x.2"];
  }
  network internal {
      address = "192.168.x.x/16";

      vm-web01 [address = "192.168.x.1"];
      vm-web02 [address = "192.168.x.2"];
      vm-db01;
      vm-db02;
  }
}
```
````

The code block above renders to this network diagram:

```nwdiag
{
  network dmz {
      address = "10.10.x.x/16"

      web01 [address = "10.10.x.1"];
      web02 [address = "10.10.x.2"];
  }
  network internal {
      address = "192.168.x.x/16";

      vm-web01 [address = "192.168.x.1"];
      vm-web02 [address = "192.168.x.2"];
      vm-db01;
      vm-db02;
  }
}
```

### Reading diagram source from file

For more complex network diagrams, there is the option to read the diagram source from a file. To do so, pass the parameter `sourcefile` as attribute of the code block:

````
```nwdiag { sourcefile="nw-simple.diag" }
```
````

Using this [source file](nw-simple.diag), the same sequence diagram as above is shown.

## Supported output formats

The default output format is `svg`. By using the `format` option (see below), you can opt for `png` or `pdf` as output format, too. 

{{%alert title="Note" color="primary" %}}
The source file needs to be a [page resource](https://gohugo.io/content-management/page-resources/) bundled to the page containing the network diagram.
{{%/alert%}}

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

If you want to make use of these option(s), you have to give them as attributes to your `nwdiag` code block, as shown in the listing below:

````
```nwdiag {format="svg" disabled=false antialias="" no-transparency="" size="30x30" no-doctype="" }
diagram source goes here
```
````

Alternatively, when reading the diagram source from a file, the parameters can be given inside the code block, too. Use the json format for notation inside the body of your block:

````
```nwdiag { sourcefile="nw-simple.diag" format="svg" disabled=false antialias="" no-transparency="" size="30x30" no-doctype="" }
{
  "format": "svg",
  "disabled": "false",
  "antialias": "",
  "no-transparency": "",
  "size": "30x30"
}
```
````
