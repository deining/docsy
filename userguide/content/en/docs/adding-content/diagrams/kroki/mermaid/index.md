---
title: "Mermaid charts and diagrams"
linkTitle: "Mermaid (charts/diagrams)"
date: 2023-03-14T21:41:11+01:00
draft: false
weight: 90
description: >
  Generate diagrams from markdown-like text, using the [Mermaid](https://mermaid.js.org/) diagramming and charting tool.
---

```mermaid-kroki {  }
graph TD
  Start --> Need{"Hugo version >= 0.93.0"}
  Need -- No --> Off["Set params.mermaid.enable = true"]
  Off --> Author
  Need -- Yes --> Author[Insert mermaid codeblock]
```

