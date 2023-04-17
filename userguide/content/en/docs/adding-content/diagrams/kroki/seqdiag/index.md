---
title: "Sequence diagrams (seqdiag)"
linkTitle: "Sequence diagrams"
date: 2023-03-14T21:38:57+01:00
draft: false
weight: 160
description: >
  Author sequence diagrams using the [seqdiag](http://blockdiag.com/en/seqdiag/) library.
---
## Overview and example diagrams

The [seqdiag library](https://github.com/blockdiag/seqdiag) allows you do generate activity diagrams via a textual description of the activity to be depicted. Use the [documentation](http://blockdiag.com/en/seqdiag/) for syntax details.
Also, you may find this [example diagram](http://blockdiag.com/en/seqdiag/examples.html) useful, too.

## Authoring your sequence diagram

To embed an sequence diagram in your page, use a `seqdiag` code block and put the diagram source in the body of the block. An example is given below:

````
```seqdiag
{
  "Docsy user"  -> "Discussion board" [label = "ask question"];
  "Discussion board" -> "Community member" [label = "read question"];
  "Community member"  -> "Docsy instance" [label = "investigate issue raised"];
  "Community member"  <-- "Docsy instance" [label = "come up with solution"];
  "Discussion board"  <-- "Community member" [label = "propose solution"];
  "Docsy user"  <-- "Discussion board" [label = "check proposed solution"];
  "Docsy user"  -> "Discussion board" [label = "mark question as resolved"];
  "Docsy user"  -> "Docsy user" [label = "Being happy"];
}
````

The code block above renders to this sequence diagram:

```seqdiag { disabled=false options=\{ "key 1": "value", "key 2": "value" \}}
{
  "Docsy user" -> "Discussion board" [label = "ask question"];
  "Discussion board" -> "Community member" [label = "read question"];
  "Community member"  -> "Docsy test instance" [label = "investigate issue raised"];
  "Community member"  <-- "Docsy test instance" [label = "come up with solution"];
  "Discussion board"  <-- "Community member" [label = "propose solution"];
  "Docsy user"  <-- "Discussion board" [label = "check proposed solution"];
  "Docsy user"  -> "Discussion board" [label = "mark question as resolved"];
  "Docsy user"  -> "Docsy user" [label = "Being happy"];
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

If you want to make use of these option(s), you have to give them as attributes to your `seqdiag` code block, as shown in the listing below:

````
```seqdiag {format="svg" disabled=false antialias="" no-transparency="" size="30x30" no-doctype="" }
diagram source goes here
```
````
