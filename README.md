# Associative Memory Programming (AMP)

> *The brain does much more than just recollect. It intercompares, it synthesizes, it analyzes, it generates abstractions.*
>
> Carl Sagan, *Cosmos*, episode 11, "The Persistence of Memory" (1980)

**AMP is a way of building software around associative memory.** Instead of writing every rule by hand, or training a
model you can't see inside, you design a structure of memory, declare the parts that must never bend, teach it the rest
by example, and read exactly what it learnt and why.

> **Status: early.** AMP is in active design. The engine is being built in Go and the notation is still settling. This
> README describes what AMP is and why it exists; it is a premise to be proven, not a list of finished features. The
> "Getting started" section sketches the intended experience and does not run yet. See [VISION.md](VISION.md) for where
> this is heading and [CONTRACT.md](CONTRACT.md) for what the system is held to.

---

## The idea in one paragraph

Software today is either **hard** or **soft**. Hand-written code is hard: exact, predictable, and too rigid for the
regularities and irregularities of real data. Deep learning is soft: it absorbs the mess, but it needs huge amounts of
data, it can't say why it did what it did, and it can't be corrected precisely. AMP sits between them. It gives the
engineer a **dial**: you decide what stays fixed and what stays loose, and you can see exactly where the line sits. What
you build can be trusted, and still accommodates the noise.

## What AMP is made of

Its building blocks come from associative memory, the kind of memory brains and nervous systems use, where a few pieces
of something bring back the whole of it.

- **The substrate** is everything a running program holds: every cell, every piece of structure, and the activity and
  heat within them. One interconnected material, held in RAM or stored on disk.
- **Volumes** are bounded parts of the substrate: cells, with a size and a **density** (how many of their cells may be
  active at once, within a range that can move). A volume may also have a **shape**, a 2D or 3D space with places and
  neighbours, so that work written into it can be seen. *(Proposed.)*
- **Cells** are the smallest unit. A cell has no strength and no weight. At any moment it may be active or not, and hot
  or not.
- **Cell sets** are sets of cells in one volume. Cues, activity and hot cells are all cell sets, combined with ordinary
  set operators.
- **Encoders** are the boundary with the outside world. They turn input into **encodings** (indexes, a label and a
  source), which a volume turns into cell sets. Encoders and volumes know nothing about each other.
- **Assemblies** are groups of cells whose connections loop back on each other. Activate part of one and the rest comes
  back. That is how AMP recognises something from a fragment.
- **Transitions** are chains that point forwards, carrying activity on to what comes next. That is how AMP follows a
  sequence, a process or a procedure. *(Not yet in the language.)*

Programs do three things with them:

- **Write** structure into a volume: an assembly, by hand or built from other structure. `fixed` structure can never be
  outcompeted.
- **Ask** a volume: `complete` returns the whole a cue completes to; `touch` returns everything a cue reaches. Rivals
  compete; a true tie is held open, not guessed. Whatever couldn't be explained is **heat**: a gap, a conflict,
  something that doesn't fit.
- **Learn**: there is no single built-in learning method. Learning procedures are written in AMP from the same
  primitives (comparing, composing, decomposing, writing), because how associative memory should learn is still an open
  research question, and different problems call for different kinds of learning.

## The tenets

These are the ideas everything else in AMP rests on.

**1. You set the dial.** A program is shaped three ways, freely mixed: **declare** structure by hand (the rules that must
never bend), **teach** it from examples, and let chosen parts **grow** on the job. What is fixed and what is loose is a
visible design decision.

**2. Heat is honest.** Where information fits together, it settles. Where it conflicts or has gaps, the heat stays, and
nothing smooths it over. AMP doesn't claim to know the truth; it is honest about its own coherence: what fits, what
doesn't, and what is missing.

**3. A glass box.** Every decision has a cause you can state, and every piece of structure traces back to its source:
what it read, what it was told, or what it worked out itself. You can ask *why it did something* and explore *what it
knows*.

**4. Nothing breaks.** Learning only adds structure. Being wrong means new structure forms and outcompetes the old.
History is never lost, so a memory can be rewound, compared across versions, and reviewed like code.

**5. Learns on the job, from little, cheaply.** No separate training phase. A handful of examples can be enough. Bits,
set operations and work only where something is active, so it runs on ordinary hardware, from a microcontroller to a
server.

**6. Any scale.** The same engine fits a sensor on a fence post and the systems of a large enterprise. The value is the
same everywhere: trust that still accommodates the mess.

**7. People stay at the helm.** An AMP program takes in the heat of a problem and gives back either action it can take
reliably, or a clear account of what would resolve it, so people can understand the problem and the solution for
themselves.

**8. A new craft.** Programming with associative memory is largely unexplored. Its idioms will be discovered by people
building, tinkering and playing.

## What could you build with it?

Wherever rules alone are too brittle and models alone are too opaque. For example:

- **Large systems you can defend.** A satellite imagery company holds each client's hard definitions fixed, learns how
  the data varies by season, sensor and region, and can show exactly why any result was issued.
- **Complex programmes.** A large construction project finds misfits between thousands of requirements, designs,
  schedules and reports, and shows what a proposed change would unsettle before anyone agrees to it.
- **Regulated decisions.** Finance, health, insurance and public services, where decisions must be explained and the
  record of what was known when must be kept.
- **Soft matching.** Deciding when two records describe the same thing, reading messy commands, routing requests.
- **Following a process.** Knowing where an order, a machine or a restoration project is in its lifecycle, even with
  missing or out-of-order events, and noticing when it drifts off every known path.
- **Sensors that learn their place.** Small devices that learn the normal of their own patch and explain their alerts.
- **Controllers with guardrails.** Regulating a pond, a building or a plant, with the rules that must never bend declared
  as fixed structure.
- **Seeing a disagreement clearly.** Mapping where groups truly disagree, and where the disagreement is really a missing
  fact.
- **Knowledge that stays with its owners.** Communities recording a language or body of knowledge that remains theirs,
  traceable to the people who gave it.
- **A memory for AI agents.** A readable, correctable memory underneath a language model, and a check on whether its
  claims fit what is known.
- **Learning.** Maps of a field that lead back to their sources, a mirror that shows a learner where their own
  understanding doesn't yet fit, and memories you teach yourself in order to learn.
- **Things made for the joy of it.** An instrument that completes your melodies, a memory that knows the birds in your
  garden, little creatures that learn.

[VISION.md](VISION.md) walks through several of these in detail.

## What AMP is not

- **Not a source of truth.** It shows what fits and what doesn't. Something false that hangs together produces no heat.
- **Not exact.** Its memory is good enough, not perfect. Exact records (recordings, documents, figures) are kept outside
  and linked to.
- **Not a replacement for people's judgement.** It makes the shape of a problem visible; people decide.
- **Not proven yet.** Much of this rests on capabilities the engine is still being built to show.

## How it fits together

AMP is three tools sharing one engine library:

| Tool | For | What it does |
|---|---|---|
| **AMP** (Associative Memory Programming) | the engine | the engine library, an interpreter for the notation, and a REPL |
| **AMX** (Associative Memory Examination) | agents and scripts | run worlds, query structure, trace runs, test, score and explain, in a machine-readable form |
| **AMT** (Associative Memory Terminal) | people | a terminal interface to watch a run, browse assemblies, and explore what was learnt, linked back to its sources |

AMX and AMT only ever read from the engine. Examination never feeds back into learning, which keeps results honest.
Because AMX is machine-readable, other systems can read through it too, such as a language model summarising what a
memory has done and what has changed.

## Getting started (a sketch)

> **None of this runs yet.** The commands and notation below show the intended experience. Names and syntax are
> provisional and will change.

Install the tools (planned):

```
go install github.com/sebjwallace/associative-memory-programming/cmd/amp@latest
```

A first program, `fruit.amp`:

```
// fruit.amp
let words: Encoder = Encoder(split: "word", cells: 1)
let fruit: Volume = Volume(size: 64, density: 2% to 10%)

let apple: Assembly[fruit] = write fruit using words <"apple", "red", "sweet"> fixed
let cherry: Assembly[fruit] = write fruit using words <"cherry", "red", "sour">

let apple_completion: Result[fruit] = complete(fruit, fruit{words{"apple"}})
let red_completion: Result[fruit] = complete(fruit, fruit{words{"red"}})

test "apple and cherry share red" {
   expect apple.cells & cherry.cells == fruit{words{"red"}}
}
```

Run it and look at what came back:

```
amp> run "fruit.amp"
amp> apple_completion
candidates   apple                 1 of 3 given, 2 recalled
heat         none
sources      fruit.amp, line 5

amp> red_completion
candidates   apple, cherry         1 of 3 each
ties         apple | cherry
heat         contested: "red"
```

Asked for "apple", the memory brings back the whole. Asked for "red", it finds two equally good answers and says so,
rather than guessing. Every answer says where it came from. Ask it directly:

```
amp> why red_completion
```

From there a program grows by the dial: **write** what must hold, **learn** from sources with a learning procedure, and
choose what may keep changing. Then **examine** it with tests, AMX and AMT.

## Where things stand

- **The language** is being designed one decision at a time. What is settled, and what is still in progress, is in the
  [language specification](language-specification/README.md), which also suggests the order in which to build it.
- **The engine and interpreter** are next: built step by step from the specification, in Go for now (the implementation
  language has no say over AMP's syntax).
- **The research** behind AMP (the theory of heat, the experiments, and how the design was reached) lives in
  [anneal-machine](https://github.com/sebjwallace/anneal-machine), which continues as the research project.
- AMP builds on a long line of work: Hebb's cell assemblies, Hopfield networks, Kanerva's sparse distributed memory and
  the hyperdimensional computing that grew from it, case-based reasoning, and neurosymbolic AI. [VISION.md](VISION.md)
  says what AMP aims to add.

## The documents

| Document | What it is |
|---|---|
| [VISION.md](VISION.md) | where AMP is heading, and what it could be like to use |
| [CONTRACT.md](CONTRACT.md) | the system contract: what AMP must be, whoever builds it |
| [LANGUAGE-CONTRACT.md](LANGUAGE-CONTRACT.md) | the language contract: what the language must be |
| [language-specification/](language-specification/README.md) | the language in detail: stable decisions and work in progress |

The contracts are the masters. The specification follows them, and the code follows the specification. The state of the
code never dictates a contract.

## Licence

- Code: Apache 2.0.
- Writing (this README, the vision, the contract and other docs): CC BY 4.0.
