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

| Diagram type                   | Output formats             | Renderer          | Supported options                                                    |
|--------------------------------|----------------------------|-------------------|----------------------------------------------------------------------|
| [Activity diagrams][]          | svg, png, pdf              | [actdiag][]       | antialias, no-transparency, size, no-doctype                         |
| [ASCII Art][]                  | svg, png, pdf              | [svgbob][]        | background, font-family, font-size, fill-color, scale, stroke-width  |
| [Block diagrams][]             | svg, png, pdf              | [blockdiag][]     | antialias, no-transparency, size, no-doctype                         |
| [Business process diagrams][]  | svg                        | [bpmn-js][]       | n/a                                                                  |
| [Byte field diagrams][]        | svg                        | [bytefield-svg][] | n/a                                                                  |
| [C4 with PlantUML][]           | svg, png, jpg, txt, base64 | [C4-PlantUML][]   | n/a                                                                  |
| [D2 diagrams][]                | svg                        | [D2][]            | n/a                                                                  |
| [Database diagrams][]          | svg                        | [dbml-renderer][] | n/a                                                                  |
| [Diagrams Through Ascii Art][] | svg, png                   | [ditaa][] | n/a                                                                  |

[Activity diagrams]: ../actdiag/
[ASCII Art]: ../svgbob/
[Block diagrams]: ../blockdiag/
[Business process diagrams]: ../bpmn/
[Byte field diagrams]: ../bytefield/
[C4 with PlantUML]: ../c4plantuml/
[D2 diagrams]: ../d2/
[Database diagrams]: ../dbml/
[Diagrams Through Ascii Art]: ../ditaa

[actdiag]: http://blockdiag.com/en/actdiag/
[svgbob]: https://github.com/ivanceras/svgbob
[blockdiag]: http://blockdiag.com/en/blockdiag/
[bpmn-js]: https://github.com/bpmn-io/bpmn-js
[bytefield-svg]: https://github.com/Deep-Symmetry/bytefield-svg
[C4-PlantUML]: https://github.com/plantuml-stdlib/C4-PlantUML
[D2]: https://d2lang.com
[dbml-renderer]: https://github.com/softwaretechnik-berlin/dbml-renderer
[ditaa]: https://ditaa.sourceforge.net/


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
