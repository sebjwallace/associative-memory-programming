# 9 · Heat

**Status: Mostly stable.** Where heat lives, the separate heat type, heat models made of heat dynamics, and built-in
heat models only are stable. The exact shape of the heat type and the definitions of each heat dynamic are in progress.

## 9.1 What heat is

**Stable.** Heat is what does not fit: a gap, a misfit, rivals that cannot both hold. It says **where** work is needed.
Heat is not an error: it is a normal part of a valid answer.

## 9.2 Where heat lives

**Stable.** Heat lives in the substrate, **at cells**. Heat and activity are different things over the same cells:

- an active cell can be cool (something explains it);
- an active cell can be hot (nothing explains it);
- an inactive cell can be hot (a gap: an assembly expects it and it is not there).

Because heat can sit on cells that are not active, heat cannot be folded into a cell set of activity.

## 9.3 The heat type

**Stable:** heat has its own type, `Heat[V]`, at cell level, separate from `CellSet[V]`. The two are not interchangeable
implicitly; a heat value gives its cells as a `CellSet[V]` when cell set operators are wanted.

**In progress: its shape.** The proposal:

- heat at a cell is a whole number (a count of heat, not a tuned weight), so heat can move and gather;
- `.cells` gives every cell with any heat, as a `CellSet[V]`;
- `.at(...)` gives the heat at a cell, as an `Int`;
- `.total` gives the heat in all, as an `Int`; `.proportion` gives it as a share of the volume, as a `Ratio`;
- heat has kinds: **unexplained** (nothing accounts for a cell) and **contested** (rivals that tie claim it), and
  possibly **missing** (a gap).

```
let fruit_heat: Heat[fruit] = fruit.heat                  // read from the volume (chapter 5)
let mixed_heat: Heat[fruit] = complete(fruit, fruit{words{"apple"}, words{"banana"}}).heat
let hot_cells: CellSet[fruit] = mixed_heat.cells
let banana_heat: Int = mixed_heat.at(words{"banana"})
```

## 9.4 Heat models

**Stable.** A heat model is a set of **heat dynamics**: the processes by which heat changes over time.

| Heat dynamic | What it governs |
|---|---|
| **Generation** | how heat forms: a cell nothing explains, rivals that cannot both hold, structure that cannot settle |
| **Transfer** | how heat moves from where it formed: to neighbouring cells, along connections, across the volume |
| **Cooling** | how heat leaves: by resolution (the misfit is explained), by formation (heat becomes structure), or by release (letting go of heat that will not settle, only when declared and visible) |
| **Response** | what heat does while present: raising density, making structure more willing to reconfigure, drawing attention |

**Accumulation is observed, not configured.** Heat gathers wherever generation and transfer bring in more than cooling
takes away. It is the outcome of the dynamics, read from heat over time, not a dynamic of its own.

**The words.** They come from thermal physics where the meaning carries over: heat generation, heat transfer,
cooling, thermal response. "Source" is avoided for generation because AMP uses it for provenance. "Dissipation" is
avoided for cooling because in physics it means useful energy turning into heat, nearly the opposite. A **cooling
schedule**, the established annealing term, may describe how cooling proceeds over time.

**In progress:** what each dynamic does in each heat model; the names of the built-in heat models.

## 9.5 Built-in heat models only

**Stable.** AMP has no custom heat models. Every heat model is part of the language, built into the engine and
optimised there. A program chooses among them; it cannot write its own.

*Why:* heat models written by each program would make programs and substrates impossible to compare or exchange, and
would run slowly inside the engine's innermost loop. With built-in heat models only, a program depends on nothing but
the language version, which can be managed with ordinary practices for forwards and backwards compatibility.

## 9.6 Heat and energy

**In progress.** In the research behind AMP, heat says where to work, and energy (the cost of the whole description) says
what to keep. Heat is local; energy belongs to the substrate as a whole. Whether energy appears in the language, for
example in what a learning procedure reports, is open and is a question for the system contract.
