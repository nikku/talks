---
title: Lean Architecture
description: Adopting our Software to fit new requirements as we go, in a reasonable manner.
origin: https://github.com/nikku/talks/tree/main/talks/2021-lean-architecture
image: https://nikku.github.io/talks/2021-lean-architecture/screenshot.png
author: Nico Rehwaldt
authorTwitter: '@nrehwaldt'
type: article
tags:
  - architecture
  - software architecture
  - lean
---

## _Lean Architecture_

#### Adopting our tools to fit new requirements, as we go.

<small><a href="https://github.com/nikku">Nico Rehwaldt</a> 2021</small>

---

### It starts with _Refactoring_.

---

<!--config
align=left
-->

### Refactoring

> _Refactoring_ consists of improving the internal structure of an existing program’s source code, while preserving its external behavior. [...]
>
> :arrow_right: [Agile Aliance](https://www.agilealliance.org/glossary/refactoring/)

---

### But thinks _Big_.

---

### Architecture

* Structure to support capabilities in a reusable, recognizable, and safe manner
* :arrow_right: Good practices baked into the core of your application

---

[<img src="https://imgs.xkcd.com/comics/dependency_2x.png" height="700" title="XKCD: Dependencies 2347" />](https://xkcd.com/2347/)

---

### Lean Architecture

* Evolve high level structure of your app, as you go
* Support new, emerging capabilities
* *Do what's necessary when it fits*
* :bulb: Get a sense of what's necessary (and when)

---


### Case Study: Sections

* Identify we are miss-using existing `Overlay` component
* Find a common denominator: A `Section` component that easily combines with `Overlay`
* [Fix what is necessary](https://github.com/camunda/camunda-modeler/pull/2571) :wrench:
* Consider the future: Unbuild legacy `Overlay` structure

---

### The _Rules of Refactoring_ Apply

:zero: Know what you want to do and why

:one: Separate refactoring from feature development

:two: Get buy in and improve substantially

:three: Clean up after you

---

## How to Identify when to Refactor / Re-Architect?

---

## Thanks

# :heart: