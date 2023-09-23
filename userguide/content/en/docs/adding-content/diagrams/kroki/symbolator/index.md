---
title: "Symbolator: component diagramming tool for VHDL and Verilog"
linkTitle: "Diagrams of digital systems (Symbolator)"
date: 2023-03-14T21:40:46+01:00
draft: false
weight: 47
description: >
  Author diagrams modeling the structure and behaviour of digital systems, using the [Symbolator](https://kevinpt.github.io/symbolator) tool.
---
## Overview and example diagrams

Using [Symbolator](https://kevinpt.github.io/symbolator/) tool, you can create component diagrams from [HDL](https://en.wikipedia.org/wiki/Hardware_description_language) source files, both from [vdhl](https://en.wikipedia.org/wiki/VHDL) and from [verilog hdl](https://en.wikipedia.org/wiki/Verilog) files. Use the [documentation](https://kevinpt.github.io/symbolator/#using-symbolator) for details on how to use Symbolator.

## Authoring your VHL component diagram

### Diagram source embedded in code block

To embed a VHL component diagram in your page, use a `symbolator` code block and put the diagram source in the body of the block. The example below shows a component diagram comprising 5 sections:

````
```symbolator
component sectioned is
  port (
    --# {{clocks|Clocking}}
    Clock : in std_ulogic;

    --# {{control|Control signals}}
    Enable: in std_ulogic;

    --# {{data|Data port}}
    Data1 : in std_ulogic;

    --# {{Additional port1}}
    Data2 : out std_ulogic;

    --# {{}}
    Data3 : inout std_ulogic
  );
end component;
```
````

The code block above renders to this VHL component diagram:

```symbolator
component sectioned is
  port (
    --# {{clocks|Clocking}}
    Clock : in std_ulogic;

    --# {{control|Control signals}}
    Enable: in std_ulogic;

    --# {{data|Data port}}
    Data1 : in std_ulogic;

    --# {{Additional port1}}
    Data2 : out std_ulogic;

    --# {{}}
    Data3 : inout std_ulogic
  );
end component;
```

### Reading diagram source from file

For more complex VHL component diagram, there is the option to read the diagram source from a file. To do so, pass the parameter `sourcefile` as attribute of the code block:

````
```symbolator { sourcefile="symbolator-simple.diag" }
```
````

Using this [source file](symbolator-simple.diag), the same VHL component diagram as above is shown.

{{%alert title="Note" color="primary" %}}
The source file needs to be a [page resource](https://gohugo.io/content-management/page-resources/) bundled to the page containing the VHL component diagram.
{{%/alert%}}

## Supported output formats

The default output format is `svg`. By using the `format` option (see below), you can opt for `png` as output format, too.

## Diagram options

Your diagram can be customized using the options listed below:

| Option name  | Allowable values           | Description                                       |
|-----------------|-------------------------|---------------------------------------------------|
| sourcefile   | string                     | Name of file containing diagram source code       |
| format       | _svg_, or _png_            | Output format of generated diagram image          |
| component    | string                     | Component to be rendered, default: last component |
| transparent  | flag,<br>empty string ("") | Transparent diagram background                    |
| title        | string                     | Title to be inserted into diagram                 |
| scale        | number                     | Scale factor for diagram, default: 1.0            |
| no-type      | flag,<br>empty string ("") | Omit type information for ports                   |
| library-name | string                     | Adds name of a library (title must be set!)       |

If you want to make use of these option(s), you have to give them as attributes to your `symbolator` code block, as shown in the listing below:

````
```symbolator { format="svg" disabled=false title="my title" library-name="my library" no-type="" scale=0.4 }
diagram source goes here
```
````

Alternatively, when reading the diagram source from a file, the parameters can be given inside the code block, too. Use the json format for notation inside the body of your block:

````
```symbolator { sourcefile="symbolator-simple.diag" }
{
  "format": "svg",
  "disabled": "false",
  "title": "my title",
  "library-name": "my library",
  "transparent": "",
  "scale": "0.4"
}
```
````
