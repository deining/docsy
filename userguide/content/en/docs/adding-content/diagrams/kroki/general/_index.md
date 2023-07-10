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

| Diagram type                        | Output formats             | Renderer          | Supported options                                                   |
|-------------------------------------|----------------------------|-------------------|---------------------------------------------------------------------|
| [Activity diagrams][]               | svg, png, pdf              | [actdiag][]       | antialias, no-transparency, size, no-doctype                        |
| [ASCII Art][]                       | svg, png, pdf              | [svgbob][]        | background, font-family, font-size, fill-color, scale, stroke-width |
| [Block diagrams][]                  | svg, png, pdf              | [blockdiag][]     | antialias, no-transparency, size, no-doctype                        |
| [Business process diagrams][]       | svg                        | [bpmn-js][]       | n/a                                                                 |
| [Byte field diagrams][]             | svg                        | [bytefield-svg][] | n/a                                                                 |
| [C4 model diagrams (PlantUML)][]    | svg, png, jpg, txt, base64 | [C4-PlantUML][]   | n/a                                                                 |
| [C4 model diagrams (Structurizr)][] | svg, png, jpg, txt, base64 | [Structurizr][]   | view-key                                                            |
| [D2 diagrams][]                     | svg                        | [D2][]            | theme, sketch                                                       |
| [Database diagrams][]               | svg                        | [dbml-renderer][] | n/a                                                                 |
| [Diagrams Through Ascii Art][]      | svg, png                   | [ditaa][]         | n/a                                                                 |
| [Drawings for LaTeX][]              | svg, png, jpg, pdf         | [PGF/TikZ][]      | n/a                                                                 |
| [Entity-Relationship diagrams][]    | svg, png, jpg, pdf         | [erd][]           | n/a                                                                 |
| [GraphViz diagrams][]               | svg, png, jpg, pdf         | [GraphViz][]      | [graph|node|edge]-attribute-{name}, layout, scale                   |
| [Hand-drawn like diagrams][]        | svg                        | [Excalidraw][]    | n/a                                                                 |
| [Interactive graphics][]            | svg, png, pdf              | [Vega Lite][]     | n/a                                                                 |
| [Interactive visualizations][]      | svg, png, pdf              | [Vega][]          | n/a                                                                 |
| [Mermaid charts and diagrams][]     | svg, png                   | [Mermaid][]       | see complete [list of options][] in Mermaid source code             |
| [Network diagrams][]                | svg, png, pdf              | [nwdiag][]        | antialias, no-transparency, size, no-doctype                        |
| [Packet diagrams][]                 | svg, png, pdf              | [nwdiag][]        | antialias, no-transparency, size, no-doctype                        |
| [Pikchr diagrams][]                 | svg                        | [Pickchr][]       | n/a                                                                 |
| [Rack diagrams][]                   | svg, png, pdf              | [nwdiag][]        | antialias, no-transparency, size, no-doctype                        |
| [Sequence diagrams][]               | svg, png, pdf              | [seqdiag][]       | antialias, no-transparency, size, no-doctype                        |
| [Timing diagrams][]                 | svg, png, jpg, pdf         | [WaveDrom][]      | n/a                                                                 |
| [UML diagrams (nomnoml)][]          | svg, png, jpg, pdf         | [nomnoml][]       | n/a                                                                 |
| [UML diagrams (PlantUML)][]         | svg, png, jpg, pdf         | [PlantUML][]      | theme                                                               |
| [UML diagrams (UMLet)][]            | svg, png, jpg, pdf         | [UMLet][]         | n/a                                                                 |
| [Wiring diagrams][]                 | svg, png, pdf              | [WireViz][]       | n/a                                                                 |

[Activity diagrams]: ../actdiag/
[ASCII Art]: ../svgbob/
[Block diagrams]: ../blockdiag/
[Business process diagrams]: ../bpmn/
[Byte field diagrams]: ../bytefield/
[C4 model diagrams (PlantUML)]: ../
[C4 model diagrams (Structurizr)]: ../structurizr
[D2 diagrams]: ../d2/
[Database diagrams]: ../dbml/
[Diagrams Through Ascii Art]: ../ditaa/
[Drawings for LaTeX]: ../tikz/
[Entity-Relationship diagrams]: ../erd/
[GraphViz diagrams]: ../graphviz/
[Hand-drawn like diagrams]: ../excalidraw/
[Interactive graphics]: ../vegalite/
[Interactive visualizations]: ../vega/
[Mermaid charts and diagrams]: ../mermaid/
[Network diagrams]: ../nwdiag/
[Packet diagrams]: ../packetdiag/
[Pikchr diagrams]: ../pikchr/
[Rack diagrams]: ../rackdiag/
[Sequence diagrams]: ../seqdiag/
[Timing diagrams]: ../wavedrom/
[UML diagrams (nomnoml)]: ../nomnoml/
[UML diagrams (PlantUML)]: ../plantuml/
[UML diagrams (UMLet)]: ../umlet/
[Wiring diagrams]: ../wireviz/

[actdiag]: http://blockdiag.com/en/actdiag/
[svgbob]: https://github.com/ivanceras/svgbob
[blockdiag]: http://blockdiag.com/en/blockdiag/
[bpmn-js]: https://github.com/bpmn-io/bpmn-js
[bytefield-svg]: https://github.com/Deep-Symmetry/bytefield-svg
[C4-PlantUML]: https://github.com/plantuml-stdlib/C4-PlantUML
[Structurizr]: https://github.com/structurizr/dsl
[D2]: https://d2lang.com
[dbml-renderer]: https://github.com/softwaretechnik-berlin/dbml-renderer
[ditaa]: https://ditaa.sourceforge.net/
[PGF/TikZ]: https://github.com/pgf-tikz/pgf
[erd]: https://github.com/BurntSushi/erd
[GraphViz]: https://gitlab.com/graphviz/graphviz
[Excalidraw]: https://excalidraw.com
[Vega Lite]: https://vega.github.io/vega-lite/
[Vega]: https://vega.github.io/vega/
[Mermaid]: https://mermaid.js.org/
[list of options]: https://github.com/mermaid-js/mermaid/blob/master/packages/mermaid/src/config.type.ts
[nwdiag]: http://blockdiag.com/en/nwdiag/
[Pickchr]: https://pikchr.org/
[seqdiag]: http://blockdiag.com/en/seqdiag/
[WaveDrom]: https://wavedrom.com/
[nomnoml]: https://www.nomnoml.com/
[PlantUML]:https://plantuml.com/
[UMLet]: https://www.umlet.com/
[WireViz]: https://github.com/wireviz/WireViz

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
