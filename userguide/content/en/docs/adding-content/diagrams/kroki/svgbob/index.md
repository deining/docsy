---
title: "ASCII Art"
linkTitle: "ASCII Art"
date: 2023-03-14T21:51:26+01:00
draft: false
weight: 20
description: >
  Author ASCII Art using the [svg-bob](https://github.com/ivanceras/svgbob) converter tool.
---
### ASCII Art

For example, the following defines a simple AsciiArt diagram:

````
```svgbob {type=svgbob format=svg}
  _____
 /  O__]
/  ___]
\   \
 |   |
 |   |
 /   /
 \   \
 /   /
```
````

```svgbob {type=svgbob format=svg disabled=false}
  _____
 /  O__]
/  ___]
\   \
 |   |
 |   |
 /   /
 \   \
 /   /
```

<br>

```svgbob { disabled=true }
 ________  ________  ________  ________       ___    ___      ___  ________           ________  ________  ________  ___       ___
|\   ___ \|\   __  \|\   ____\|\   ____\     |\  \  /  /|    |\  \|\   ____\         |\   ____\|\   __  \|\   __  \|\  \     |\  \      
\ \  \_|\ \ \  \|\  \ \  \___|\ \  \___|_    \ \  \/  / /    \ \  \ \  \___|_        \ \  \___|\ \  \|\  \ \  \|\  \ \  \    \ \  \     
 \ \  \ \\ \ \  \\\  \ \  \    \ \_____  \    \ \    / /      \ \  \ \_____  \        \ \  \    \ \  \\\  \ \  \\\  \ \  \    \ \  \    
  \ \  \_\\ \ \  \\\  \ \  \____\|____|\  \    \/  /  /        \ \  \|____|\  \        \ \  \____\ \  \\\  \ \  \\\  \ \  \____\ \__\   
   \ \_______\ \_______\ \_______\____\_\  \ __/  / /           \ \__\____\_\  \        \ \_______\ \_______\ \_______\ \_______\|__|   
    \|_______|\|_______|\|_______|\_________\\___/ /             \|__|\_________\        \|_______|\|_______|\|_______|\|_______|   ___ 
                                 \|_________\|___|/                  \|_________|                                                  |\__\
                                                                                                                                   \|__|
```

## Diagram options

Your diagram can be customized using the options listed below: 

| Option name     | Allowable values                                  | Description                                  |
|-----------------|---------------------------------------------------|----------------------------------------------|
| sourcefile      | string                                            | Name of file containing diagram source code  |
| format          | _svg_, _png_ or _pdf_                             | Output format of generated diagram image     |
| disabled        | boolean,<br>_true_ or _false_                     | Disable/skip diagram                         |
| background      | string,<br>white                                  | Fill color for backdrop background           |
| font-family     | any,<br>arial                                     | Font family for rendered text                |
| font-size       | integer,<br>14                                    | Font size for rendered text                  |
| fill-color      | anx,<br>black                                     | Fill color for solid shapes                  |
| scale           | any,<br>1                                         | Scale factor for the entire SVG              |
| stroke-width    | any,<br>2                                         | Stroke width for all lines                   |

If you want to make use of these option(s), you have to give them as attributes to your `svgbob` code block, as shown in the listing below:

````
```svgbob { format="svg" disabled=false backgound="green" font-size=12 scale=0.9 }
diagram source goes here
```
````

Alternatively, when reading the diagram source from a file, the parameters can be given inside the code block, too. Use the json format for notation inside the body of your block:

````
```svgbob { sourcefile="svg-bob-simple.diag" format="svg" disabled=false disabled=false backgound="green" font-size=12 scale=0.9 }
{
  "format": "svg",
  "disabled": "false",
  "background": "green",
  "font-size": "12",
  "scale": "0.9"
}
```
````