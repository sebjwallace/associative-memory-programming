# 7 · Structure: assemblies, writing and learning

**Status: Mostly stable.** Assemblies, `fixed`, composition from cell sets, and the decision that learning is written
in AMP from primitives are stable. The verb `write`, the `using` form, `sample`, and the visibility of learnt versus
written structure are in progress.

## 7.1 Activity and structure

**Stable.** AMP keeps two things apart:

- **Activity** is which cells are on: a `CellSet` read from a volume (chapter 5). It is a description and does nothing
  by itself.
- **Structure** is the connections between cells that exist in a volume whether or not anything is active: assemblies,
  and later transitions.

## 7.2 Assemblies

**Stable.** An assembly is a group of cells whose connections loop back on each other, so that enough of it being
active brings back the rest. The type is `Assembly[V]`.

An `Assembly` value is a **reference** to a piece of structure, not a container: assemblies share cells (apple and
cherry both use "red"), and an assembly value points at structure in the volume so it can be examined, tested and
composed. It cannot be edited: values are immutable, and the substrate never changes structure in place. Different
structure is new structure, which competes with the old.

```
let apple_cells: CellSet[fruit] = apple.cells     // the cells it binds
let apple_is_fixed: Bool = apple.fixed
let apple_source: Source = apple.source           // where it came from
```

## 7.3 Writing structure

**Stable in meaning; the verb is in progress.** The one statement that puts structure into a volume returns the new
assembly. The proposed verb is `write`.

```
let words: Encoder = Encoder(split: "word", cells: 4)
let fruit: Volume = Volume(size: 256, density: 2% to 10%)

let apple: Assembly[fruit] = write fruit using words <"apple", "red", "sweet"> fixed
let cherry: Assembly[fruit] = write fruit using words <"cherry", "red", "sour">
let red_things: Assembly[fruit] = write fruit <apple.cells & cherry.cells>
```

- Angle brackets contain what the assembly binds: labels, or a cell set.
- Labels must say which encoder they come from: either each label in full (`<words{"apple"}, words{"red"}>`) or the
  encoder named once for the statement with `using`. Which form the language keeps is **in progress**.
- Writing changes the substrate, so it is only allowed on a volume the function may change (chapter 10).

## 7.4 `fixed`

**Stable.** `fixed` marks structure that can never be outcompeted: whatever is formed later, fixed structure always
wins where it applies. It is how programs declare the rules that must never bend (guardrails).

`fixed` says nothing about who or what made the structure. That is the source's job (section 7.7). Hand-written
structure is often fixed but need not be: a default may be left open to be overruled.

## 7.5 Composition, abstraction and decomposition

**Stable in principle.** The three ways of making new structure from existing structure are expressed with cell set
operators (chapter 5) and writing. They correspond to synthesis, abstraction and analysis.

```
// Composition (synthesis): a whole made from a sample of each part.
let pair_cells: CellSet[fruit] = sample(apple.cells, 25%) + sample(cherry.cells, 25%)
let fruit_pair: Assembly[fruit] = write fruit <pair_cells>

// Abstraction: what the parts share becomes a whole of its own.
let red_cells: CellSet[fruit] = apple.cells & cherry.cells        // "red"
let red_things: Assembly[fruit] = write fruit <red_cells>

// Decomposition (analysis): what is left when the shared part is taken out.
let only_apple_cells: CellSet[fruit] = apple.cells - cherry.cells  // "apple", "sweet"
```

**`sample` is in progress.** A super-assembly binds a subsample of its parts' cells rather than all of them (a finding of
the research behind AMP: sparse binding works better than full connection). The proposal:

- `sample(cells, ratio)` returns a `CellSet`, a subset of the cells given.
- It is **deterministic**: the same cells and ratio always give the same sample. The language defines the rule; nothing
  is left to chance.
- Each part is sampled separately and the samples combined, so that every part keeps a foothold in the whole: the
  whole can bring back each part, and each part the whole. Sampling the union of the parts instead can leave a small
  part barely represented.

**Open:** the sampling rule itself; and whether `<apple, cherry>` survives as shorthand for composing with a default
sample, or composition is always written out.

## 7.6 Learning is written in AMP

**Stable.** The language has **no built-in learning method**. It provides the primitives every learning method is
built from (reading a volume, completing and touching, cell set operators, sampling, writing), and learning procedures
are ordinary functions written from them.

*Why:* the right way for associative memory to learn is still a research question. Annealing is one candidate, and the
research is finding others that may be more principled. The language should not bet on one theory; it should make every
candidate expressible. Different kinds of intelligence learn differently, as different animals do on much the same
biological material, so learning that fits the problem is part of what AMP is for.

Learning procedures do not threaten interoperability, unlike custom heat models (chapter 9): whatever procedure formed
it, structure is ordinary structure, cells and assemblies with sources, so substrates built in different ways can still
be read, compared and exchanged.

```
// A learning procedure: learn what is new in a line by comparing it with what is already known.
fn learn_by_overlap(fruit: mut Volume, words: Encoder, line_text: Text) -> List[Assembly[fruit]] {
   let line: CellSet[fruit] = fruit{words.encode(line_text)}
   let reading: Result[fruit] = complete(fruit, line)
   let nearest: Assembly[fruit] = reading.best                 // the best-supported known assembly
   let shared: CellSet[fruit] = nearest.cells & line          // abstraction: what they share
   let new_part: CellSet[fruit] = line - shared               // decomposition: what is new
   let abstraction: Assembly[fruit] = write fruit <shared>
   let novelty: Assembly[fruit] = write fruit <sample(shared, 25%) + new_part>
   return [abstraction, novelty]
}
```

(`reading.best`, and what a procedure should do when `reading` holds a tie, depend on the result design in chapter 8.)

What the language guarantees for every learning procedure, whoever wrote it: structure is only ever added, never edited;
sources are attached automatically; and the procedure is deterministic. What the language cannot check is whether a
procedure genuinely resolves heat rather than hiding it. That is governed by the system contract and by testing.

A standard library may provide well-tested learning procedures, so that not every program starts from nothing.

## 7.7 Learnt and written structure are visible

**Stable in principle; the mechanism is in progress.** Programming is hard-wiring: that is legitimate, and it is the
point of the dial between fixed and loose. But a program must not hard-wire by accident while appearing to learn. So the
language makes the balance between what was written and what was learnt visible.

The proposal:

- **Cell origins are tracked.** Every cell in new structure is traced back through the program to where it came from:
  the input (encodings of data the procedure was given), or the program itself (a label or index written in the code).
- **Every assembly is classed** as learnt (only from input), written (only from the program) or mixed, and its source
  records which procedure formed it and from what.
- **Tooling warns** where a procedure that appears to learn writes structure from literals in the code, branches on
  particular content, or uses bare numbers as settings.

```
fn learn_by_overlap(fruit: mut Volume, words: Encoder, line_text: Text) -> List[Assembly[fruit]] {
   let line: CellSet[fruit] = fruit{words.encode(line_text)}
   let shared: CellSet[fruit] = line & fruit{words{"red"}}
   //                                  ^^^^^^^^^^^^^^^^^^^
   // warning: this procedure writes structure from a label in the code ("red").
   //          Structure formed from it will be classed as written, not learnt.
   ...
}
```

Tests that only running can do are described in chapter 11 (relabelling, held-out input, empty input).

No tool can catch everything: a procedure with no literals and no content branches can still have its settings tuned
until it happens to work on one set of data. Held-out and relabelling tests reduce that risk; they cannot remove it.

## 7.8 Changes to the substrate are marked

**Stable in principle; spelling in progress.** Writing is the only statement that changes the substrate's structure,
and every learning procedure is built on it. A function that writes, or calls a function that writes, must say so in
its signature (chapter 10).
