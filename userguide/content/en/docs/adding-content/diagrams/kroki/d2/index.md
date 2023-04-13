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
