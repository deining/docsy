---
title: "Wiring diagrams (WireViz)"
linkTitle: "Wiring diagrams"
date: 2023-03-14T21:34:22+01:00
draft: false
weight: 200
description: >
  Author wiring diagrams using the [WireViz](https://github.com/formatc1702/WireViz) tool.
---

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

connections:
  -
    - X1: [1-2]
    - W1: [1-2]
    - X2: [1-2]
```
