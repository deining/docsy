---
title: "General concept and overview"
linkTitle: "General concept"
date: 2023-04-13T14:47:28+02:00
draft: false
weight: 1
description: >
  Using the kroki online service, you can embed 26 different diagram types into your pages.
---
## Kroki: an overwiew

[Kroki](https://kroki.io) is a free web service for rendering diagrams of all kind, in total you can choose between 26 different [diagram types](https://kroki.io/#support):

| Diagram type        | Output formats   | Renderer                                      | Supported options                            |
|---------------------|------------------| ----------------------------------------------|----------------------------------------------|
| [Activity diagrams](../actdiag/)       | svg, png, pdf    | [actdiag](http://blockdiag.com/en/actdiag/)   | antialias, no-transparency, size, no-doctype |
| [ASCII Art](../actdiag/)               | svg, png, pdf    | [svgbob](https://github.com/ivanceras/svgbob) | background, font-family, font-size, fill-color, scale, stroke-width  |

```kroki { type="graphviz" disabled=true }
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
## Using your own local kroki service

You can also [deploy and use your own server](https://docs.kroki.io/kroki/setup/install/) to deliver diagrams. In this case update hugo's configuration file to point to that server:

{{< tabpane >}}
{{< tab header="Configuration file:" disabled=true />}}
{{< tab header="hugo.toml" lang="toml" >}}
[params.kroki]
kroki_server = "https://local.kroki.tld"
{{< /tab >}}
{{< tab header="hugo.yaml" lang="yaml" >}}
params:
  kroki:
    kroki_server: 'https://local.kroki.tld'
{{< /tab >}}
{{< tab header="hugo.json" lang="json" >}}
{
  "params": {
    "kroki": {
      "kroki_server": "https://local.kroki.tld"
    }
  }
}
{{< /tab >}}
{{< /tabpane >}}
