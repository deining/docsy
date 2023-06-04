---
title: "D2 diagrams"
linkTitle: "D2 diagrams"
date: 2023-03-14T21:39:56+01:00
draft: false
weight: 40
description: >
  Author D2 diagrams using the [D2](https://d2lang.com/) scripting language.
---
```d2 { theme = 4 }
dogs -> cats -> mice: chase
replica 1 <-> replica 2
a -> b: To err is human, to moo bovine {
  source-arrowhead: 1
  target-arrowhead: * {
    shape: diamond
  }
}
```

## Diagram options

Your diagram can be customized using the options listed below: 

| Option name     | Allowable values                                  | Description                                  |
|-----------------|---------------------------------------------------|----------------------------------------------|
| sourcefile      | string                                            | Name of file containing diagram source code  |
| format          | _svg_                                             | Output format of generated diagram image     |
| disabled        | boolean,<br>_true_ or _false_                     | Disable/skip diagram                         |
| sketch          | flag,<br>empty string ("")                        | Render diagram with a [hand-drawn aesthetic](https://d2lang.com/tour/sketch/) |
| theme           | string or number:<br>- _default_ (0)<br>- _neutral-grey_ (1)<br>- _flagship-terrastruct_ (3)<br>- _cool-classics_ (4)<br>- _mixed-berry-blue_ (5)<br>- _grape-soda_ (6)<br>- _aubergine_ (7)<br>- _colorblind-clear_ (8)<br>- _vanilla-nitro-cola_ (100)<br>- _orange-creamsicle_ (101)<br>- _shirley-temple_ (102)<br>- _earth-tones_ (103)<br>- _everglade-green_ (104)<br>- _buttered-toast_ (105)<br>- _dark-mauve_ (200)<br>- _terminal_ (300)<br>- _terminal-grayscale_ (301) | See [list of themes](https://d2lang.com/tour/themes/)                              |


If you want to make use of these option(s), you have to give them as attributes to your `d2` code block, as shown in the listing below:

````
```d2 { format="svg" disabled=false sketch=true theme="buttered-toast" }
diagram source goes here
```
````

Alternatively, when reading the diagram source from a file, the parameters can be given inside the code block, too. Use the json format for notation inside the body of your block:

````
```d2 { sourcefile="d2-simple.diag" format="svg" disabled=false sketch=true theme="buttered-toast" }
{
  "format": "svg",
  "disabled": "false",
  "sketch": "true",
  "theme": "buttered-toast"
}
```
````