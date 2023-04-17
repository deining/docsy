---
title: "Packet diagrams (packetdiag)"
linkTitle: "Packet diagrams"
date: 2023-03-14T21:39:13+01:00
draft: false
weight: 120
description: >
  Author packet diagrams using the [nwdiag](http://blockdiag.com/en/nwdiag/) library.
---
## Overview and example diagrams

The [nwdiag library](https://github.com/blockdiag/nwdiag/tree/master/src/packetdiag) allows you do generate packet diagrams via a textual description of the packet to be depicted. Use the [documentation](http://blockdiag.com/en/nwdiag/packetdiag-examples.html) for syntax details.
Also, you may find this [example diagram](https://github.com/blockdiag/nwdiag/tree/master/examples/packetdiag) useful, too.

## Authoring your packet diagram

To embed a packet diagram in your page, use a `packetdiag` code block and put the diagram source in the body of the block. The example below shows the structure of an TCP/IP packet: 

````
```packetdiag
diagram {
  colwidth = 32
  node_height = 72

  0-15: Source Port
  16-31: Destination Port
  32-63: Sequence Number
  64-95: Acknowledgment Number
  96-99: Data Offset
  100-105: Reserved
  106: URG [rotate = 270]
  107: ACK [rotate = 270]
  108: PSH [rotate = 270]
  109: RST [rotate = 270]
  110: SYN [rotate = 270]
  111: FIN [rotate = 270]
  112-127: Window
  128-143: Checksum
  144-159: Urgent Pointer
  160-191: (Options and Padding)
  192-223: data [colheight = 3]
}
```
````

The code block above renders to this packet diagram:

```packetdiag
diagram {
  colwidth = 32
  node_height = 72

  0-15: Source Port
  16-31: Destination Port
  32-63: Sequence Number
  64-95: Acknowledgment Number
  96-99: Data Offset
  100-105: Reserved
  106: URG [rotate = 270]
  107: ACK [rotate = 270]
  108: PSH [rotate = 270]
  109: RST [rotate = 270]
  110: SYN [rotate = 270]
  111: FIN [rotate = 270]
  112-127: Window
  128-143: Checksum
  144-159: Urgent Pointer
  160-191: (Options and Padding)
  192-223: data [colheight = 3]
}
```

## Supported output formats

The default output format is `svg`. By using the `format` option (see below), you can opt for `png` or `pdf` as output format, too. 

## Diagram options

Your diagram can be customized using the options listed below: 

| Option name     | Allowable values                                  | Description                                  |
|-----------------|---------------------------------------------------|----------------------------------------------|
| format          | _svg_, _png_ or _pdf_                             | Output format of generated diagram image     |
| disabled        | boolean,<br>_true_ or _false_                     | Disable/skip diagram                         |
| antialias       | flag,<br>empty string ("")                        | Pass diagram image to anti-alias filter      |
| no-transparency | flag,<br>empty string ("")                        | No transparent diagram background (PNG only) |
| size            | dimensions,<br>_width_x_height_<br>e.g. _320x240_ | Size of diagram                              |
| no-doctype      | flag,<br>empty string ("")                        | Omit doctype definition tags (SVG only)      |

If you want to make use of these option(s), you have to give them as attributes to your `packetdiag` code block, as shown in the listing below:

````
```packetdiag {format="svg" disabled=false antialias="" no-transparency="" size="30x30" no-doctype="" }
diagram source goes here
```
````
