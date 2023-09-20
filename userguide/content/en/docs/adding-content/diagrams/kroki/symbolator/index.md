---
title: "Symbolator: component diagramming tool for VHDL and Verilog"
linkTitle: "Diagrams of digital systems (Symbolator)"
date: 2023-03-14T21:40:46+01:00
draft: false
weight: 47
description: >
  Author diagrams modeling the structure and behaviour of digital systems, using the [Symbolator](https://kevinpt.github.io/symbolator) tool.
---

```symbolator
module demo_device #(
    //# {{}}
    parameter SIZE = 8,
    parameter RESET_ACTIVE_LEVEL = 1
) (
    //# {{clocks|Clocking}}
    input wire clock,
    //# {{control|Control signals}}
    input wire reset,
    input wire enable,
    //# {{data|Data ports}}
    input wire [SIZE-1:0] data_in,
    output wire [SIZE-1:0] data_out
);
  // ...
endmodule
```
