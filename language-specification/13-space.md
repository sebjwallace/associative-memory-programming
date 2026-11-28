# 13 · Space: shaped volumes

**Status: In progress.** This chapter is theoretical: nothing in it is decided. It is in the specification because the
research behind AMP gives it a strong precedent, and because it shapes the language: what a volume can be, how a program
can be seen thinking, and how AMP takes in and gives back things laid out in space (pages, images, models).

## 13.1 Why space

In the research, associative memory learned to carry out whole procedures (long multiplication, from one cue, with no
controller), and much of what made that possible was **space**. Work was written at places, as on a page. A focus read,
wrote and moved over those places. The places a procedure used were relative to where it started, not fixed values. It
is the idea of a Turing machine, a machine reading and writing a tape as it moves along it, with the tape made into a
grid.

Two lessons came with it.

- **It worked.** Content bound to places, read by a moving focus, was what let the memory hold its working, carry values
  from step to step, and run a procedure to the end.
- **The places lived in the code.** The grid, its coordinates, and the arithmetic of moving across it ("one place to the
  left", "the row below") were worked out by the program around the memory, not by the memory. The memory held "this is
  at that place"; how places related to each other was outside it. And because relations were held as exact positions,
  something learned on one layout could not be reached on a different layout of the same kind of thing.

So space is valuable, and the language needs to give it a home inside the substrate, in a way that does not hand the
thinking back to code.

## 13.2 What and where are two sides of one coin

**The picture.** Space is not a separate kind of memory. The assemblies a volume holds can bind what things are
together with where they are relative to each other. A remembered thing carries its own layout: which part sits above,
beside or a little further along from which. Content-addressable and spatially addressable memory are the same
substrate, read two ways.

This is why a shaped volume (below) is not a new kind of thing, only a volume with geometry. What is learned about space
lives where everything else learned lives: in assemblies.

## 13.3 Shaped volumes

**Proposal.** A volume may declare a **shape** instead of a size: the number of places along each dimension, in any
number of dimensions. Its cells are then also addressable by coordinates, counted from 1, and the engine knows which
places neighbour which.

```
let words: Encoder = Encoder(split: "word", cells: 1)

let fruit: Volume = Volume(size: 256, density: 2% to 10%)           // a volume as before
let table: Volume = Volume(shape: [12, 8], density: 1% to 5%)       // a 2D space: 12 by 8 places
let bowl: Volume = Volume(shape: [32, 32, 32], density: 1% to 3%)   // a 3D space

let corner: CellSet[table] = table.at(1, 1)          // the cells at one place, by coordinates
```

- **Density** has its usual meaning: the proportion of cells active at once. In a shaped volume, that is how much of the
  space is drawn or attended to at a moment.
- **Addressing.** Braces already mean a set of indexes (`fruit{3, 7}`), so coordinates need a form of their own:
  `table.at(1, 1)` is proposed. The spelling is open.
- **Not a new type.** A shaped volume is a `Volume`; its cell sets are `CellSet`s; everything in chapters 5 to 9 applies
  unchanged.

## 13.4 The canvas never does the thinking

**Proposed rule.** A shaped volume provides **geometry and nothing else**: places, and which places are neighbours.
It never reasons. In particular:

- **No coordinate arithmetic as reasoning.** "One place to the left" is not a calculation a program makes on the
  memory's behalf. A move is **structure**: a transition from one place to another, declared or learned (transitions are
  not yet in the language).
- **Relations live in assemblies.** What is learned about space ("below", "next to", "a little further along") is bound
  into assemblies with content, as relations, not stored as positions in the canvas.
- **A focus is a cell set.** Where attention is, in a shaped volume, is a cell set of that volume like any other; moving
  it is the same kind of step as any other change of activity.

*Why:* this is the lesson of 13.1. Space handed to code becomes code doing the thinking; space given to the substrate as
geometry, with relations learned in structure, keeps the thinking where it can be seen and checked.

## 13.5 Seeing, and imagining

**The picture.** A shaped volume is the part of the substrate you can see. It works in both directions:

- **Perception.** An encoder lays something out in the space (a page of text, an image, a 3D model), and the rest of
  the substrate recognises it.
- **Imagination.** Structure completes, and the completion is drawn into the space. Cue "ripe" and the ripe apple
  appears; cue "unripe" and the green one does.

So neither volume is the puppet master: the connection runs both ways, and which way activity flows is the difference
between seeing and imagining.

The order of things is: the world, an encoder, a shaped volume, the rest of the substrate, and back out through a
decoder. The encoder and decoder sit at the edge and only convert; the shaped volume is inside, part of the substrate.

**A twin that runs.** When transitions join in, the structure does not only complete one picture: it steps from state to
state, and the space shows each one. An apple ripening from green to red, moment by moment, drawn in the space from what
the substrate has learned about apples. Simulation you can watch: a digital twin made of associative memory.

## 13.6 Understandability and testing

A shaped volume makes the substrate's work visible as it happens: a sum written out with its carries, a shape built up in
3D, a remembered layout coming back. Tools (AMT) would draw shaped volumes as grids or 3D views.

It also makes testing concrete. A test can say what the space should look like after a cue:

```
test "unripe apples are green" {
   let unripe_apple: Result[fruit] = complete(fruit, fruit{words.encode("apple unripe")})
   expect table.activity == drawing_of_green_apple       // what the space should show
}
```

(How a completion in one volume is drawn into another depends on how volumes connect, which is not yet designed.)

## 13.7 Nearby places sharing cells

**Open, and worth trying.** If each place is a single cell, "the place below" and "two places below" share nothing,
and relations become exact. If places are encoded so that nearby places share cells (as a reading of a level can be
encoded as a band of cells, so nearby levels overlap), then "below", "a little to the left" and "somewhere further
along" overlap naturally. Relations would then be loose in the right way, which may be what lets something learned on
one layout reach a different layout of the same kind.

## 13.8 Open questions

- Whether shape is declared on a volume (as proposed) or is something an encoder gives.
- The syntax for addressing by coordinates.
- Whether a shaped volume holds activity more steadily than other volumes (the tape's stability), and whether that is
  just a matter of its settings.
- Whether structure ever forms inside a shaped volume, or only activity is held there and structure lives elsewhere.
- How a shaped volume connects to other volumes, which belongs with how volumes connect in general (chapter 14).
- How places should be encoded, single cells or overlapping ones (13.7).
- Moves and focus, which wait on transitions.
