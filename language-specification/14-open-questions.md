# 14 · Open questions

**Status: In progress.** Everything here is undecided. Each item names where it belongs.

## Syntax

- The verb for putting structure into a volume (`write` is proposed). *Chapter 7.*
- Whether labels inside an assembly name their encoder once (`using words`) or each time. *Chapter 7.*
- The marker for a parameter whose volume a function changes (`mut` is proposed). *Chapter 10.*
- The symbols for cell set operators (`+`, `&`, `-`, `^`, `==`, `in` are proposed). *Chapter 5.*
- The syntax for a range of indexes. *Chapter 5.*
- Explicit `defer` versus automatic clean-up of temporary volumes. *Chapter 4.*
- Whether `<apple, cherry>` is shorthand for composition with a default sample. *Chapter 7.*

## Types

- The shape of `Heat[V]`: heat per cell as a count, its kinds, and how totals are given. *Chapter 9.*
- The fields of `Result[V]`, the name for one candidate answer, and how a result reports more than one level of
  structure. *Chapter 8.*
- Generic functions over volumes, and stopping values from outliving their volume. *Chapters 3, 4.*
- Whether a cell set carries the labels and sources of its cells. *Chapter 5.*
- Whether a `State` type (a volume's whole condition at a moment) is ever needed. *Chapters 3, 5.*

## Behaviour

- What moves a volume's density within its range, and whether density is a ceiling only. *Chapter 5.*
- When a reading of a volume's activity or heat is taken, as activity unfolds over moments. *Chapter 5.*
- How activity unfolds over a sequence of encodings, step by step. *Chapters 5, 6.*
- The deterministic rule behind `sample`. *Chapter 7.*
- How learnt, written and mixed structure are tracked, and what tooling warns about. *Chapter 7.*
- The full set of primitives that ask the substrate, beyond `complete` and `touch`. *Chapter 8.*
- Whether cell set operators apply to heat and to results. *Chapters 5, 8, 9.*
- What each heat dynamic does in each built-in heat model, and their names. *Chapter 9.*
- Whether energy appears in the language. *Chapter 9; the system contract.*
- How volumes connect to each other, and how a program settles: AMP's own model of computation. *Not yet a chapter.*
- Space: shaped volumes, addressing by coordinates, moves as structure, a focus as a cell set, perception and
  imagination through one connection, and how places are encoded. *Chapter 13.*

## Running programs

- Compilation: compiling frozen substrates for speed, or compact forms for small devices. *Chapter 1.*
- Whether reaching a loop's limit is an error or part of the result. *Chapter 12.*
