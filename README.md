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

- **Cells** are the smallest unit. A cell is active or not. There are no strengths and no weights.
- **Volumes** hold cells, and can hold other volumes. A volume has behaviour of its own, such as how many of its cells
  may be active at once, and so what competes inside it.
- **Connections** run from cell to cell, always in one direction, and arrive at a cell in groups called **gates**. A gate
  opens when enough of its connections are active. *(The final name for a connection is still open.)*
- **Assemblies** are groups of cells that point at each other in a loop. Activate part of one and the rest comes back.
  That is how AMP recognises something from a fragment.
- **Transitions** are chains that point forwards, carrying activity on to what comes next. That is how AMP follows a
  sequence, a process or a procedure.

The engine does two things with them:

- **invoke** reads. Input arrives, the memory completes it towards what it already knows, rival explanations compete, and
  the better supported one wins. A true tie is held open, not guessed.
- **anneal** learns. Whatever invoke couldn't explain is left as **heat**: a gap, a conflict, something that doesn't
  fit. Annealing forms new structure that resolves it.

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

Start the REPL and give the memory something to learn. Three letters arrive, one moment after another:

```
amp> invoke c, a, t
moment 1   c   incomplete   heat !c
moment 2   a   incomplete   heat !a
moment 3   t   incomplete   heat !t
```

Nothing explained any of them, so each moment left heat (`!`). Invoking alone learns nothing. Annealing resolves the
heat by forming structure:

```
amp> anneal
forms #1 = <c, a, t>       an assembly: any part brings back the rest
forms #2 = c -> a -> t     a transition: the order they came in
heat 3 -> 0
```

Now give it part of what it learnt:

```
amp> invoke c
moment 1   c
moment 2   +a     invoked by c
moment 3   +t     invoked by a
complete   #1 <c, a, t>   3 of 3
```

The `+` marks what the memory brought back by itself, and every line says why. Ask it directly:

```
amp> why moment 2
```

From there a program grows by the three moves of the dial: **declare** what must hold, **teach** by example, and choose
what may keep learning. Then **examine** it with AMX (tests are cues with expected completions, plus where heat should
and shouldn't appear) and look inside with AMT.

## Where things stand

- The engine and interpreter are being built in Go.
- The notation is being settled one step at a time. Terms are agreed deliberately, and a few names are still open.
- The research behind AMP (the theory of heat, the experiments, and how the design was reached) lives in
  [anneal-machine](https://github.com/sebjwallace/anneal-machine), which continues as the research project.
- AMP builds on a long line of work: Hebb's cell assemblies, Hopfield networks, Kanerva's sparse distributed memory and
  the hyperdimensional computing that grew from it, case-based reasoning, and neurosymbolic AI. [VISION.md](VISION.md)
  says what AMP aims to add.

## Licence

- Code: Apache 2.0.
- Writing (this README, the vision, the contract and other docs): CC BY 4.0.