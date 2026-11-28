# 5 · Volumes, cells and cell sets

**Status: Stable**, except where marked.

## 5.1 Volumes

**Stable.** A volume is a bounded part of the substrate: a set of cells with behaviour of its own. A volume is a value,
created by calling its constructor, anywhere a value can be created: at the top of a file for a volume that lasts, or
inside a function for a temporary one.

```
let fruit: Volume = Volume(size: 64, density: 2% to 10%)
```

A volume declares:

- **`size`**: how many cells it has, an `Int`. Cells are numbered from 1 to `size`.
- **`density`**: the proportion of its cells that may be active at once, as a range of `Ratio`s. The lower end is where
  density normally rests; the upper end is how far it may rise. Density is dynamic: it moves within the range as the
  volume runs.

A volume knows nothing about encoders (chapter 6). It is pure: cells and their behaviour.

**Why density, and why a range.** "Density" has one reading, the proportion that is active, where "sparsity" is used
both ways in the literature. A proportion means the same thing at any volume size. A range lets activity rise when it
needs to (for example, to find missing context) and settle back.

**In progress:** what moves density within its range (the engine's own dynamics, a program within limits, or both);
and whether density is a ceiling only (the proposal: at most this proportion active) or can also be a target.

Sizes and densities may be computed with ordinary arithmetic:

```
const cells_per_word: Int = 4

fn sized_volume(word_count: Int, words_active: Int, headroom: Int) -> Volume {
   let size: Int = word_count * cells_per_word
   let most_active: Int = words_active * cells_per_word
   let resting_density: Ratio = Ratio(most_active, size)
   let highest_density: Ratio = resting_density * headroom
   return Volume(size: size, density: resting_density to highest_density)
}

let fruit_names: Volume = sized_volume(word_count: 200, words_active: 1, headroom: 3)
// 800 cells, density 1/200 to 3/200
```

## 5.2 Cells

**Stable.** A cell is the smallest unit of the substrate. It has no strength, weight or level. Every cell belongs to
exactly one volume. At any moment a cell may be active or not, and may hold heat or not (chapter 9): the two are
independent.

A program refers to cells in two ways:

- **By index:** a bare number, the cell's position in its volume. `fruit{7}` is cell 7 of fruit.
- **By label:** quoted text, the name an encoder gave to some indexes (chapter 6). `words{"red"}` is the encoding
  words gave to "red", which a volume turns into its own cells: `fruit{words{"red"}}`.

The quotes keep the two apart: `fruit{12}` is cell 12, while a label "12" would be written `words{"12"}`.

**Indexes are checked.** An index outside a volume is an error, reported before anything runs where it can be:

```
fruit{70}
// error: index 70 is outside fruit (1..64)
```

## 5.3 Cell sets

**Stable.** A cell set is a set of cells in one volume, and nothing more. It says which cells; it does not say whether
they are active, hot, or anything else. The type is `CellSet[V]`.

Cell sets are what programs work with: a cue is a cell set, an assembly is made of a cell set, the hot cells of a heat
value are a cell set, and the activity of a volume is a cell set.

```
let red: CellSet[fruit] = fruit{words{"red"}}
let cell_seven: CellSet[fruit] = fruit{7}
let apple: CellSet[fruit] = fruit{apple_line}     // from a list of encodings: all its steps at once
```

A cell set's type names its volume. A cell set with no cells is valid, not an error.

**Why not "state".** Earlier drafts called this type `State`. In physics a system's state is its whole condition at a
moment. In AMP that is more than which cells are active: it includes where the volume is hot, and its current density.
So a plain set of cells is a `CellSet`, and the word **state** is kept for a volume's whole condition, should the
language ever need a type for it (for example, to save or rewind a snapshot). No `State` type exists yet.

**In progress:** whether a cell set carries the labels and sources of its cells (so that operations keep them), or
whether provenance lives only in encodings, assemblies and results.

## 5.4 Reading a volume

**Stable in principle.** A volume can be asked for its current activity and its current heat. Each reading is a
snapshot: an immutable value describing the volume at that moment. The volume carries on; the snapshot does not change.

```
let fruit_activity: CellSet[fruit] = fruit.activity     // which cells are active now
let fruit_heat: Heat[fruit] = fruit.heat                 // where it is hot now, and how much (chapter 9)
```

**In progress:** when, in the running of a program, a reading is taken, given that a volume's activity unfolds over
moments.

## 5.5 Operators on cell sets

**Stable in principle: cell set operations are written with operators, not function calls, and there is one way to
write each. The symbols are in progress.**

A cell set is bits underneath, one per cell, so the operators most programmers know for bits and sets carry over
exactly. The proposal:

| Operation | Operator | Gives |
|---|---|---|
| union | `+` | cells in either |
| intersection | `&` | cells in both |
| difference | `-` | cells in the first and not the second |
| symmetric difference | `^` | cells in one but not both |
| equality | `==` | whether two cell sets hold the same cells |
| containment | `in` | whether one cell set lies within another |

The bar `|` is not used for union because AMP already uses it for a held tie. Angle brackets are not used for
comparison because AMP uses them for assemblies, which is why containment is the word `in`.

These are plain set operations on cells. They do not consult the substrate, form no structure and produce no heat, so
they return a `CellSet`, not a `Result`.

```
let words: Encoder = Encoder(split: "word", cells: 1)
let fruit: Volume = Volume(size: 64, density: 2% to 10%)

let apple: CellSet[fruit] = fruit{words.encode("apple red sweet")}
let cherry: CellSet[fruit] = fruit{words.encode("cherry red sour")}
let lemon: CellSet[fruit] = fruit{words.encode("lemon yellow sour")}
let red: CellSet[fruit] = fruit{words{"red"}}

let apple_or_lemon: CellSet[fruit] = apple + lemon        // everything in either
let apple_and_cherry: CellSet[fruit] = apple & cherry     // what they share: "red"
let only_apple: CellSet[fruit] = apple - cherry           // "apple", "sweet"
let where_they_differ: CellSet[fruit] = apple ^ cherry    // "apple", "sweet", "cherry", "sour"
let nothing_shared: CellSet[fruit] = apple & lemon        // empty, and valid

let apple_is_red: Bool = red in apple
let same_cells: Bool = apple_and_cherry == red
let apple_size: Int = apple.size
```

Mixing volumes is a type error:

```
let other: Volume = Volume(size: 32, density: 5%)
apple & other{3}
// error: can't intersect a CellSet of fruit with a CellSet of other
```

**In progress:** whether the same operators apply to heat (for example, adding two heats cell by cell); whether they
apply to results, carrying heat through; and the syntax for a range of indexes.
