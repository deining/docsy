---
title: "Byte field diagrams"
linkTitle: "Byte field diagrams"
date: 2023-03-14T21:38:41+01:00
draft: false
weight: 30
description: >
  Author byte field diagrams using the [bytefield-svg](https://github.com/Deep-Symmetry/bytefield-svg) node module.
---

## Overview

The [bytefield-svg node module](https://github.com/Deep-Symmetry/bytefield-svg) allows you do generate diagrams for network protocols, memory layouts, or similar binary structures via a textual description. Use the [documentation](https://bytefield-svg.deepsymmetry.org) for syntax details.

## Authoring your byte field diagram

### Diagram source embedded in code block

To embed an byte field diagram in your page, use a `bytefield` code block and put the diagram source in the body of the block. An example is given below:

````
```bytefield
(draw-column-headers)
(draw-box "Address" {:span 4})
(draw-box "Size" {:span 2})
(draw-box 0 {:span 2})
(draw-gap "Payload")
(draw-bottom)
```
````
The code block above renders to this byte field diagram:

```bytefield
(draw-column-headers)
(draw-box "Address" {:span 4})
(draw-box "Size" {:span 2})
(draw-box 0 {:span 2})
(draw-gap "Payload")
(draw-bottom)
```

<p/>

A more advanced byte field diagram (generated from this [source file](https://raw.githubusercontent.com/Deep-Symmetry/bytefield-svg/main/test.edn)) might look like:

```bytefield
(defattrs :bg-green {:fill "#a0ffa0"})
(defattrs :bg-yellow {:fill "#ffffa0"})
(defattrs :bg-pink {:fill "#ffb0a0"})
(defattrs :bg-cyan {:fill "#a0fafa"})
(defattrs :bg-purple {:fill "#e4b5f7"})

(defn draw-group-label-header
  "Creates a small borderless box used to draw the textual label headers
  used below the byte labels for remotedb message diagrams.
  Arguments are the number of columns to span and the text of the
  label."
  [span label]
  (draw-box (text label [:math {:font-size 12}]) {:span    span
                                                  :borders #{}
                                                  :height  14}))

(defn draw-remotedb-header
  "Generates the byte and field labels and standard header fields of a
  request or response message for the remotedb database server with
  the specified kind and args values."
  [kind args]
  (draw-column-headers)
  (draw-group-label-header 5 "start")
  (draw-group-label-header 5 "TxID")
  (draw-group-label-header 3 "type")
  (draw-group-label-header 2 "args")
  (draw-group-label-header 1 "tags")
  (next-row 18)

  (draw-box 0x11 :bg-green)
  (draw-box 0x872349ae [{:span 4} :bg-green])
  (draw-box 0x11 :bg-yellow)
  (draw-box (text "TxID" :math) [{:span 4} :bg-yellow])
  (draw-box 0x10 :bg-pink)
  (draw-box (hex-text kind 4 :bold) [{:span 2} :bg-pink])
  (draw-box 0x0f :bg-cyan)
  (draw-box (hex-text args 2 :bold) :bg-cyan)
  (draw-box 0x14 :bg-purple)

  (draw-box (text "0000000c" :hex [[:plain {:font-weight "light" :font-size 16}] " (12)"])
            [{:span 4} :bg-purple])
  (draw-box (hex-text 6 2 :bold) [:box-first :bg-purple])
  (doseq [val [6 6 3 6 6 6 6 3]]
    (draw-box (hex-text val 2 :bold) [:box-related :bg-purple]))
  (doseq [val [0 0]]
    (draw-box val [:box-related :bg-purple]))
  (draw-box 0 [:box-last :bg-purple]))

;; Figure 48: Cue point response message.

(draw-remotedb-header 0x4702 9)

(draw-box 0x11)
(draw-box 0x2104 {:span 4})
(draw-box 0x11)
(draw-box 0 {:span 4})
(draw-box 0x11)
(wrap-svg [:a {:href "https://deepsymmetry.org" :target "_blank"}]
  (draw-box (text "length" [:math] [:sub 1]) {:span 4}))
(draw-box 0x14)

(wrap-link "https://google.com"
  (draw-box (text "length" [:math] [:sub 1]) {:span 4}))
(wrap-link "https://clojure.org" {:target "_blank"}
  (draw-gap "Cue and loop point bytes"))

(draw-box nil :box-below)
(draw-box 0x11)
(draw-box 0x36 {:span 4})
(draw-box 0x11)
(draw-box (text "num" [:math] [:sub "hot"]) {:span 4})
(draw-box 0x11)
(draw-box (text "num" [:math] [:sub "cue"]) {:span 4})

(draw-box 0x11)
(draw-box (text "length" [:math] [:sub 2]) {:span 4})
(draw-box 0x14)
(draw-box (text "length" [:math] [:sub 2]) {:span 4})
(draw-gap "Unknown bytes" {:min-label-columns 6})
(draw-bottom)
```

### Reading diagram source from file

For more complex byte field diagrams, there is the option to read the diagram source from a file. To do so, pass the parameter `sourcefile` as attribute of the code block:

````
```bytefield { sourcefile="bytefield-advanced.edn" }
```
````

Using this [source file](bytefield-advanced.edn), the same diagram as depicted above is shown.

## Supported output formats

The only supported output format is `svg`.

## Diagram options

Your diagram can be customized using the options listed below: 

| Option name     | Allowable values                                  | Description                                  |
|-----------------|---------------------------------------------------|----------------------------------------------|
| sourcefile      | string                                            | Name of file containing diagram source code  |
| disabled        | boolean,<br>_true_ or _false_                     | Disable/skip diagram                         |

If you want to make use of these option(s), you have to give them as attributes to your `bytefield` code block, as shown in the listing below:

````
```bytefield { disabled=false }
diagram source goes here
```
````
