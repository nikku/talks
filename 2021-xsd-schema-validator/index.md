## Learnings From Debugging the Undebuggable

#### TLDR: Do NOT Compile Java on the Fly

<small style="font-size: .5em">Nico Rehwaldt</small>


---

## Context

* Migrated Travis CI :arrow_right: GitHub actions
* `bpmn-moddle` test suite times out ([ref](https://github.com/bpmn-io/bpmn-moddle/actions/runs/773752949))
* [Random fail?](https://github.com/bpmn-io/bpmn-moddle/runs/2408872398?check_suite_focus=true#step:6:56) :arrow_right: __NO__

---

## What is Going on?

`bpmn-moddle` uses `xsd-schema-validator`

`xsd-schema-validator` uses Java for actual validation

Java is being compiled on the fly...

---

## So...

```
{
  "name": "xsd-schema-validator",
  "scripts": {
    ...,
    "postinstall": "COMPILE JAVA HELPER"
  }
}
```