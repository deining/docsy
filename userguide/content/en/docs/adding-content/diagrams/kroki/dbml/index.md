---
title: "Database diagrams (DBML)"
linkTitle: "Database diagrams"
date: 2023-03-14T21:40:08+01:00
draft: false
weight: 45
description: >
  Author database diagrams described with [DBML](https://github.com/holistics/dbml), using the [DBML renderer](https://github.com/softwaretechnik-berlin/dbml-renderer).
---
## Overview and example diagrams

The Kroki service allows you to generate database diagram described in [Database Markup Language](https://dbml.dbdiagram.io), an [open-source DSL language](https://github.com/holistics/dbml) designed to define and document database schemas and structures. Under the hood, Kroki uses the [DBML renderer](https://github.com/softwaretechnik-berlin/dbml-renderer) to generate the SVG database diagrams. There exists a free, simple [drawing app](https://dbdiagram.io/) to interactively design database diagrams. See the [documentation](https://dbdiagram.io/docs/) for details on how to successfully make use of this app. From the source of your database diagram, you can also create your [database documentation] via a free web-based [service](https://dbdocs.io/).

## Authoring your activity diagram

### Diagram source embedded in code block

To embed a database diagram in your page, use a `dbml` code block and put the diagram source code in the body of the block. An example is given below:

````
```dbml
Table follows {
  following_user_id integer
  followed_user_id integer
  created_at timestamp
}
Table users {
  id integer [primary key]
  username varchar
  role varchar
  created_at timestamp
}
Table posts {
  id integer [primary key]
  title varchar
  body text [note: 'Content of the post']
  user_id integer
  status varchar
  created_at timestamp
}
Ref: posts.user_id > users.id // many-to-one
Ref: users.id < follows.following_user_id
Ref: users.id < follows.followed_user_id
```
````

The code block above renders to this database diagram:

```dbml
Table follows {
  following_user_id integer
  followed_user_id integer
  created_at timestamp
}
Table users {
  id integer [primary key]
  username varchar
  role varchar
  created_at timestamp
}
Table posts {
  id integer [primary key]
  title varchar
  body text [note: 'Content of the post']
  user_id integer
  status varchar
  created_at timestamp
}
Ref: posts.user_id > users.id // many-to-one
Ref: users.id < follows.following_user_id
Ref: users.id < follows.followed_user_id
```

### Reading diagram source from file

For more complex database diagrams, there is the option to read the diagram source from a file. To do so, pass the parameter `sourcefile` as attribute of the code block:

````
```dbml { sourcefile="dbml-simple.diag" }
```
````

Using this [source file](dbml-simple.diag), the same database diagram as above is shown.


{{%alert title="Note" color="primary" %}}
The source file needs to be a [page resource](https://gohugo.io/content-management/page-resources/) bundled to the page containing the database diagram.
{{%/alert%}}

## Supported output formats

The only supported output format is `svg`.

## Diagram options

Your diagram can be customized using the options listed below:

| Option name     | Allowable values                                  | Description                                  |
|-----------------|---------------------------------------------------|----------------------------------------------|
| sourcefile      | string                                            | Name of file containing diagram source code  |
| disabled        | boolean,<br>_true_ or _false_                     | Disable/skip diagram                         |

If you want to make use of these option(s), you have to give them as attributes to your `dbml` code block, as shown in the listing below:

````
```dbml { disabled=false }
diagram source goes here
```
````
