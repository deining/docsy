---
title: "Wiring diagrams"
linkTitle: "Wiring diagrams (wireviz)"
date: 2023-03-14T21:34:22+01:00
draft: false
weight: 200
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
