# 3 · Types

**Status: Mostly stable.** Static, explicit typing and the core types are stable. Function types are in progress.

## 3.1 Typing rules

**Stable.**

- **Static.** Every value has a type known before the program runs. Type errors are reported before anything runs.
- **Explicit.** Every variable, constant, parameter and return value has its type written next to it. Nothing is
  inferred, even where a tool could infer it.

```
let fruit: Volume = Volume(size: 64, density: 2% to 10%)
let apple_cue: CellSet[fruit] = fruit{words{"apple"}}
```

*Why:* clarity, and reviewability, above all where code is written by agents and read by people.

## 3.2 Ordinary types

**Stable.**

| Type | Holds |
|---|---|
| `Int` | a whole number |
| `Ratio` | an exact fraction of two whole numbers; percentages are ratios |
| `Bool` | `true` or `false` |
| `Text` | text |
| `List[T]` | an ordered list of values of type `T`, counted from 1 |

**No floating point. Stable.** AMP has no floating-point numbers by default: their results can differ slightly between
machines, which would break determinism and the promise that an interpreter and a compiler always agree. Non-whole
quantities are `Ratio`s, which are exact. Floating point may be added later as an explicit opt-in, only if it is ever
genuinely needed.

## 3.3 AMP's own types

**Stable unless marked.**

| Type | Holds | Chapter |
|---|---|---|
| `Volume` | a bounded part of the substrate: cells, with a size and a density | 5 |
| `CellSet[V]` | a set of cells in volume `V` | 5 |
| `Encoder` | the boundary with the outside world | 6 |
| `Encoding` | one step of encoded input: indexes, a label and a source | 6 |
| `Assembly[V]` | a piece of structure in volume `V` | 7 |
| `Result[V]` | an answer from volume `V` | 8 (in progress) |
| `Heat[V]` | the heat of cells in volume `V` | 9 |
| `HeatModel` | one of AMP's built-in heat models | 9 |
| `Source` | where something came from | 6 |

**The word "state" is reserved** for a volume's whole condition at a moment (its activity, heat and density together).
No `State` type exists yet (chapter 5).

**Types carry their volume.** `CellSet[fruit]`, `Assembly[fruit]`, `Heat[fruit]` and `Result[fruit]` all name the
volume they belong to. Passing a value of one volume where another volume's value is expected is a type error.

## 3.4 Function types and generics

**In progress.** Functions that work on any volume need a type parameter over volumes:

```
fn count_hot_cells[V: Volume](heat: Heat[V]) -> Int { ... }
```

Because volumes are values rather than ordinary types, this needs care. In particular, a function must not return a
value of a volume that stops existing when the function ends (chapter 4); the type system is expected to catch that.
