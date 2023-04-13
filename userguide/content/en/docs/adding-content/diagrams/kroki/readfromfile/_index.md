---
title: "Reading diagram source from file"
title: "Reading source from file"
date: 2023-04-13T14:46:23+02:00
draft: false
weight: 2
description: >
  Using the shortcode *kroki*, you can read the diagram source from a file.
---
{{< kroki type="actdiag" format="svg" sourceFile="diagram.txt" >}}
{
  "no-doctype": "true"
}
{{< /kroki >}}

My file
  _____
 /  O__]
/  ___]
\   \
 |   |
 |   |
 /   /
 \   \
 /   /

