---
title: "UML diagrams (PlantUML)"
linkTitle: "UML diagrams (PlantUML)"
date: 2023-03-14T21:41:51+01:00
draft: false
weight: 179
description: >
  Author UML diagrams, using [PlantUML](https://plantuml.com).
---

## Overview and example diagrams

The [mermaid](https://mermaid.js.org) diagramming and charting tool lets you create diagrams and visualizations via a textual description. Mermaid provides several different diagram types, like sequence, class and state diagram, Pie or quadrant chart, mindmap, timeline and many more. Use the [documentation](https://mermaid.js.org/intro/) for syntax details.
You may have a look at the provided [example diagrams](https://mermaid.js.org/syntax/examples.html) to see what's possible with mermaid.

{{% alert title="Note" %}}
This page describes how to retrieve a mermaid diagram using the [kroki online diagram service](https://kroki.io). As an alternative, you can generate your [mermaid diagram natively](/docs/adding-content/diagrams/mermaid/), using docsy's built-in `mermaid` shortcode.
{{% /alert %}}

## Authoring a sequence diagram (example use case)

### Diagram source embedded in code block

To embed a sequence diagram in your page, use a `plantuml-kroki` code block and put the diagram source in the body of the block. An example is given below:

````
```plantuml-kroki
== Question ==
!theme cerulean
"Docsy user" -> "Discussion board": Ask question
activate "Docsy user"
activate "Discussion board"
"Discussion board" -> "Community member": read question
activate "Community member"
== Answer ==
loop Different strategies
"Community member" -> "Test instance": Investigate issue raised
activate "Test instance"
note left of "Test instance": After hours of investigation:
end
"Test instance" -> "Community member": Come up with solution
deactivate "Test instance"
"Community member" -> "Discussion board": Propose solution
deactivate "Community member"
"Discussion board" -> "Docsy user": check proposed solution
deactivate "Discussion board"
"Docsy user" -> "Discussion board": Mark question as resolved
"Docsy user" -> "Docsy user": Being happy
```
````

The code block above renders to this sequence diagram:

```plantuml-kroki { theme="amigo"}
@startuml
!theme cerulean
== Question ==
"Docsy user" -> "Discussion board": Ask question
activate "Docsy user"
activate "Discussion board"
"Discussion board" -> "Community member": read question
activate "Community member"
== Answer ==
loop Different strategies
"Community member" -> "Test instance": Investigate issue raised
activate "Test instance"
note left of "Test instance": After hours of investigation:
end
"Test instance" -> "Community member": Come up with solution
deactivate "Test instance"
"Community member" -> "Discussion board": Propose solution
deactivate "Community member"
"Discussion board" -> "Docsy user": check proposed solution
deactivate "Discussion board"
"Docsy user" -> "Discussion board": Mark question as resolved
"Docsy user" -> "Docsy user": Being happy
@enduml
```

### Reading diagram source from file

For more complex diagrams, there is the option to read the diagram source from a file. To do so, pass the parameter `sourcefile` as attribute of the code block:

````
```plantuml-kroki { sourcefile="plantuml-sequence.diag" }
```
````

Using this [source file](plantuml-sequence.diag), the same diagram as above is shown.

## Supported output formats

The default output format is `svg`. By using the `format` option (see below), you can opt for `png`, `jpg`, `base64` or `pdf` as output format, too. 

## Diagram options

Your diagram can be customized using the options listed below: 

| Option name     | Allowable values                                  | Description                                  |
|-----------------|---------------------------------------------------|----------------------------------------------|
| sourcefile      | string                                            | Name of file containing diagram source code  |
| format          | _svg_, _png_, _jpg_, _txt_ or _base64_            | Output format of generated diagram image     |
| disabled        | boolean,<br>_true_ or _false_                     | Disable/skip diagram                         |

Furthermore, there a many mermaid config options, provided by mermaid. For the full ist of options, have a look at the [Mermaid source code](https://github.com/mermaid-js/mermaid/blob/master/packages/mermaid/src/config.type.ts).

If you want to make use of these option(s), you have to give them as attributes to your `actdiag` code block, as shown in the listing below:

````
```plantuml-kroki { format="svg" disabled=false theme="forest" }
diagram source goes here
```
````

Alternatively, when reading the diagram source from a file, the parameters can be given inside the code block, too. Use the json format for notation inside the body of your block:


```plantuml-kroki { sourcefile="plantuml-sequence.diag" format="svg" }
{
  "theme" : "superhero"
}
```

## Base 64 image

```plantuml-kroki { format="base64" }
participant participant as Foo
actor       actor       as Foo1
boundary    boundary    as Foo2
control     control     as Foo3
entity      entity      as Foo4
database    database    as Foo5
collections collections as Foo6
queue       queue       as Foo7
Foo -> Foo1 : To actor
Foo -> Foo2 : To boundary
Foo -> Foo3 : To control
Foo -> Foo4 : To entity
Foo -> Foo5 : To database
Foo -> Foo6 : To collections
Foo -> Foo7: To queue
```

## SVG image

```plantuml-kroki { format="svg" }
participant participant as Foo
actor       actor       as Foo1
boundary    boundary    as Foo2
control     control     as Foo3
entity      entity      as Foo4
database    database    as Foo5
collections collections as Foo6
queue       queue       as Foo7
Foo -> Foo1 : To actor
Foo -> Foo2 : To boundary
Foo -> Foo3 : To control
Foo -> Foo4 : To entity
Foo -> Foo5 : To database
Foo -> Foo6 : To collections
Foo -> Foo7: To queue
```
