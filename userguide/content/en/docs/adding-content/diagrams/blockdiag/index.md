---
title: "Block diagrams"
date: 2023-03-14T21:37:56+01:00
draft: false
weight: 20
---
## Block diagrams

Documentation: [blockdiag][]

````
```blockdiag
{
  Docsy -> supports -> "block diagrams";
  Docsy -> is -> "awesome!";

  Docsy [color = "greenyellow"];
  "block diagrams" [color = "pink"];
  "awesome!" [color = "orange"];
}
```
````

```blockdiag { disabled=false }
{
  Docsy -> supports -> "block diagrams";
  Docsy -> is -> "awesome!";

  Docsy [color = "greenyellow"];
  "block diagrams" [color = "pink"];
  "awesome!" [color = "orange"];
}
```

[blockdiag]: http://blockdiag.com/en/blockdiag/

