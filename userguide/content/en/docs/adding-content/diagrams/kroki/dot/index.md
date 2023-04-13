---
title: "GraphViz diagrams (Dot language)"
linkTitle: "Dot language (GraphViz)"
date: 2023-03-31T21:33:43+02:00
draft: false
weight: 49
description: >
  Author diagrams using [GraphViz](https://www.graphviz.org/), using the [dot language](https://www.graphviz.org/doc/info/lang.html).
---

```dot { format="png"}
graph Transparency {
	layout=neato
	start=11 // empiric value to set orientation
	bgcolor="#0000ff11"
	node [shape=circle width=2.22 label="" style=filled]
	5 [color="#0000ff80"]
	6 [color="#ee00ee80"]
	1 [color="#ff000080"]
	2 [color="#eeee0080"]
	3 [color="#00ff0080"]
	4 [color="#00eeee80"]
	1 -- 2 -- 3 -- 4 -- 5 -- 6 -- 1
}
```