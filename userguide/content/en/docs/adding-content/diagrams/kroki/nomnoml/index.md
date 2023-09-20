---
title: "UML diagrams (nomnoml)"
linkTitle: "UML diagrams (nomnoml)"
date: 2023-03-14T21:41:24+01:00
draft: false
weight: 178
description: >
  Author UML diagrams, using the [nomnoml](https://www.nomnoml.com/) rendering tool.
---
```nomnoml
[<start>start] -> [<state>plunder] -> [<choice>more loot] -> [start]
[more loot] no ->[<end>e]

[Pirate|
  [beard]--[parrot]
  [beard]-:>[foul mouth]
]

[<table>mischief| bawl | sing || yell | drink ]

[<abstract>Marauder]<:--[Pirate]
[Pirate] - 0..7[mischief]
[<actor id=sailor>Jolly;Sailor]
[sailor]->[Pirate]
[sailor]->[rum]
[Pirate]-> *[rum|tastiness: Int|swig()]
```
