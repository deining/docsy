---
title: "Sequence diagrams"
linkTitle: "Sequence diagrams (seqdiag)"
date: 2023-03-14T21:38:57+01:00
draft: false
weight: 160
---
## Sequence diagrams

Documentation: [seqdiag][]

````
```seqdiag
{
  "Docsy user"  -> "Discussion board" [label = "ask question"];
  "Discussion board" -> "Community member" [label = "read question"];
  "Community member"  -> "Docsy instance" [label = "investigate issue raised"];
  "Community member"  <-- "Docsy instance" [label = "come up with solution"];
  "Discussion board"  <-- "Community member" [label = "propose solution"];
  "Docsy user"  <-- "Discussion board" [label = "check proposed solution"];
  "Docsy user"  -> "Discussion board" [label = "mark question as resolved"];
  "Docsy user"  -> "Docsy user" [label = "Being happy"];
}
````

```seqdiag { disabled=false options=\{ "key 1": "value", "key 2": "value" \}}
{
  "Docsy user" -> "Discussion board" [label = "ask question"];
  "Discussion board" -> "Community member" [label = "read question"];
  "Community member"  -> "Docsy test instance" [label = "investigate issue raised"];
  "Community member"  <-- "Docsy test instance" [label = "come up with solution"];
  "Discussion board"  <-- "Community member" [label = "propose solution"];
  "Docsy user"  <-- "Discussion board" [label = "check proposed solution"];
  "Docsy user"  -> "Discussion board" [label = "mark question as resolved"];
  "Docsy user"  -> "Docsy user" [label = "Being happy"];
}
```

[seqdiag]: http://blockdiag.com/en/seqdiag/

