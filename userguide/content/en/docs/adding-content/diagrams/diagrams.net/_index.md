---
title: "Edit your diagrams online (diagrams.net)"
linkTitle: "Online editable diagrams"
date: 2023-04-13T12:28:25+02:00
draft: false
weight: 40
description: >
  Choose among 25 different diagrams types provided by the free [Kroki](https://kroki.io) online diagram service.
---
[Diagrams.net](https://diagrams.net/) (aka `draw.io`) provides a free and open source diagram editor that can generate a wider range of diagrams than Mermaid or PlantUML using a web or desktop editor.

SVG and PNG files exported with the tool contain the source code of the original diagram by default, which allows the diagrams.net site to import those images again for edit in the future. With `draw.io` enabled, Docsy will detect this and automatically add an `Edit` button over any image that can be edited using the online site.

Hover over the image below and click edit to instantly start working with it.  Clicking the `Save` button will cause the edited diagram to be exported using the same filename and filetype, and downloaded to your browser.

{{%alert title="Note"  color="primary" %}}
If you're creating a new diagram, be sure to `File -> Export` in either `svg` or `png` format (`svg` is usually the best choice) and ensure the `Include a copy of my diagram` is selected so it can be edited again later.
{{%/alert%}}

As the diagram data is transported via the browser, the diagrams.net server does not need to access the content on your Docsy server directly at all.

{{< figure src="docsy-diagrams.svg" caption="Mouse over the above image and click the `Edit` button!">}}

To enable detection of diagrams, update `hugo.toml`/`hugo.yaml`/`hugo.json`:

{{< tabpane >}}
{{< tab header="Configuration file:" disabled=true />}}
{{< tab header="hugo.toml" lang="toml" >}}
[params.drawio]
enable = true
{{< /tab >}}
{{< tab header="hugo.yaml" lang="yaml" >}}
params:
  drawio:
    enable: true
{{< /tab >}}
{{< tab header="hugo.json" lang="json" >}}
{
  "params": {
    "drawio": {
      "enable": true
    }
  }
}
{{< /tab >}}
{{< /tabpane >}}

You can also [deploy and use your own server](https://github.com/jgraph/docker-drawio/blob/master/README.md) for editing diagrams, in which case update the configuration to point to that server:

{{< tabpane >}}
{{< tab header="Configuration file:" disabled=true />}}
{{< tab header="hugo.toml" lang="toml" >}}
[params.drawio]
drawio_server = "https://app.mydrawioserver.example.com"
{{< /tab >}}
{{< tab header="hugo.yaml" lang="yaml" >}}
params:
  drawio:
    drawio_server: 'https://app.mydrawioserver.example.com'
{{< /tab >}}
{{< tab header="hugo.json" lang="json" >}}
{
  "params": {
    "drawio": {
      "drawio_server": "https://app.mydrawioserver.example.com"
    }
  }
}
{{< /tab >}}
{{< /tabpane >}}
