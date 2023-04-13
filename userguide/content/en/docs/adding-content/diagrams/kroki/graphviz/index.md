---
title: "Graphviz: graphs and diagrams"
linkTitle: "Graphviz (graphs/diagrams)"
date: 2023-03-14T21:41:00+01:00
draft: false
weight: 70
description: >
  Author graphs or diagrams, using [Graphviz](https://www.graphviz.org/) graph drawing tools.
---

```graphviz {type=GraphViz disabled=false format="svg" scale=72.0 }
digraph D {
  subgraph cluster_p {
    label = "Kroki";
    subgraph cluster_c1 {
      label = "Server";
      Filebeat;
      subgraph cluster_gc_1 {
        label = "Docker/Server";
        Java;
      }
      subgraph cluster_gc_2 {
        label = "Docker/Mermaid";
        "Node.js";
        "Puppeteer";
        "Chrome";
      }
    }
    subgraph cluster_c2 {
      label = "CLI";
      Golang;
    }
  }
}
```
