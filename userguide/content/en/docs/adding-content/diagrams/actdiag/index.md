---
title: "Activity diagrams"
date: 2023-03-14T21:33:57+01:00
draft: false
---
## Activity diagrams

Documentation: [actdiag][]

````
```actdiag
{
  write -> convert -> image

  lane Sysadmin {
    write [label = "Setup docsy"];

  }
  lane Writer {
    label = "Technical writer"
    convert [label = "Author content"];
  }
  lane Boss {
    image [label = "Approve gratification"];
  }
}
````

```actdiag {disabled=false antialias=true no-transparency=true no-doctype=false format=png size="30x30"}
{
  write -> convert -> image

  lane Sysadmin {
    write [label = "Setup docsy"];

  }
  lane Writer {
    label = "Technical writer"
    convert [label = "Author content"];
  }
  lane Boss {
    image [label = "Approve gratification"];
  }
}
```

[actdiag]: http://blockdiag.com/en/actdiag/
