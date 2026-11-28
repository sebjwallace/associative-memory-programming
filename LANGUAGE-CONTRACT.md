# Contract · The language · proposed

*Drafted by the assistant from the owner's decisions so far. It holds only what has already been established, but
explains each point fully, so that a reader (human or agent) arriving cold can apply it without guessing. It will grow
as the language matures. Not in force until the owner signs.*

## What this contract covers

AMP has two contracts. The **system contract** (CONTRACT.md) says what AMP must be: how its substrate learns, what it
keeps, what it may never do. This **language contract** says what the language that people and agents write must be:
how programs look, what they may express, and what they must make visible.

The two are related but separate. The system contract governs the engine, whatever language drives it. This one
governs the language, whatever engine runs it. Where they touch (for example, both require that learning is visible),
each states the rule in its own terms.

Like the system contract, this one is the master. The interpreter, the engine and any examples follow it; they never
dictate it. When code and contract disagree, either the code is wrong or the contract must be changed deliberately by
its owner, never quietly by the code.

## How to read it

- **Goals** say where the language is going. A goal is met once and stays met. In order of priority.
- **Optimizations** are directions, never finished, balanced against each other. In order of priority: when two pull
  apart, the higher one wins, and a large loss to a higher one is never bought with a small gain to a lower one.
- **Constraints** say what is off the table. **Rules** are chosen to protect the goals and don't give way.
  **Conflicts** are things that are possible but would break another clause.
- **Capabilities** say what is on the table: what the language offers.
- **Principles** say what to prefer when several valid choices are open. Each gives way to something.

Every clause has a code. A code is a name, not a position: it stays with its clause if the clause moves.

Examples use arithmetic and the syntax as it stands. The syntax is provisional; the clauses are what matter. Where an
example and a clause disagree, the clause wins.

---

## Definitions

Words agreed with the owner. Where a word is still open, it is marked.

- **Substrate.** Everything a running program holds: every cell in every volume, the structure between them, and the
  activity and heat within them, whether held in RAM or stored on disk. One interconnected material.
- **Cell.** The smallest unit of the substrate. Active or not, nothing more. Every cell belongs to exactly one volume.
- **Volume.** A container of cells, with behaviour of its own: its size, and its density (how many of its cells may be
  active, which may move within a declared range). A volume knows nothing about encoders.
- **Index.** A cell's position in its volume, numbered from 1.
- **Encoder.** The boundary with the outside world: it turns input (text, readings, sound, images) into encodings. It
  knows nothing about volumes.
- **Encoding.** What an encoder returns for one step of input: a set of indexes, the label they stand for, and the
  source they came from. A whole input is a list of encodings, one per step. An encoding belongs to no volume.
- **Label.** The name an encoder gave to some indexes, such as "3". Written in quotes.
- **Cell set.** A set of cells in one volume, and nothing more: it says which cells, not whether they are active or hot.
  Cues, the cells of an assembly, a volume's activity and the hot cells of a heat value are all cell sets. Type
  `CellSet[V]`.
- **Activity.** Which cells of a volume are active at a moment: a cell set read from the volume.
- **State.** Reserved for a volume's whole condition at a moment (its activity, heat and density together). No type
  for it exists yet.
- **Result.** What every question to the substrate returns: one or more candidate cell sets, each with how well it fitted, together with
  the heat, any ties held open, the cue that was asked, the sources involved and the version of the substrate that answered.
- **Heat.** What is left unexplained: a gap, a misfit, rivals that can't both hold. Heat is not an error.
- **Primitive.** An operation built into the engine, such as `complete`, `touch`, or a cell set operator.
- **Function.** An operation written in AMP, built from primitives and other functions.
- **Assembly.** A piece of structure in a volume: cells whose connections loop back on each other, so enough of it
  active brings back the rest. An assembly value refers to structure; it is not a container.
- **Ratio.** An exact fraction of two whole numbers. Percentages are ratios.
- **Heat model.** One of AMP's built-in sets of heat dynamics.
- **Heat dynamic.** A process by which heat changes over time: generation, transfer, cooling or response.

---

## The sheet

**Goals** (in order of priority)
- **LG-GOL-1** Clear: a script says plainly what it does.
- **LG-GOL-2** Explicit: nothing is implied.
- **LG-GOL-3** Expresses AMP: declaring, teaching and growing the substrate, asking it questions, reading its results.
- **LG-GOL-4** Recognisable: readable on first sight by someone who knows a modern language.

**Optimizations** (in order of priority)
- **LG-OPZ-1** Simplicity: the fewest constructs giving the most value.
- **LG-OPZ-2** Reviewability: easy to check by someone who didn't write it.
- **LG-OPZ-3** Familiarity: modern conventions wherever they fit.

**Constraints**
- *Rules*
- **LG-CON-1** Static types, written out everywhere. *Hard.*
- **LG-CON-2** The substrate changes only where it is marked. *Hard.*
- **LG-CON-3** A result can't be ignored, and heat is never dropped. *Hard.*
- **LG-CON-4** Values are immutable. *Hard.*
- **LG-CON-5** Nothing hidden. *Hard.*
- **LG-CON-6** Deterministic. *Hard.*
- **LG-CON-7** Every loop that might not end has a limit. *Hard.*
- **LG-CON-8** Volumes and encoders are independent. *Hard.*
- **LG-CON-9** The engine's implementation language has no influence on AMP's syntax. *Hard.*
- **LG-CON-12** No floating point, unless one day explicitly opted into. *Hard.*
- **LG-CON-13** Heat models are built in. Programs cannot define their own. *Hard.*
- *Conflicts*
- **LG-CON-10** No implicit types (breaks LG-CON-1, LG-GOL-2).
- **LG-CON-11** No global state reached for unseen (breaks LG-CON-5).

**Capabilities**
- **LG-CAP-1** Volumes are values, created anywhere.
- **LG-CAP-2** Cells addressed by index or by label.
- **LG-CAP-3** Encoders return encodings; volumes turn encodings into cell sets.
- **LG-CAP-4** A cell set's type carries its volume.
- **LG-CAP-5** A small core of primitives and a standard library written in AMP.
- **LG-CAP-6** Operators on cell sets.
- **LG-CAP-9** Learning written in AMP, from primitives.
- **LG-CAP-7** Tests built into the language.
- **LG-CAP-8** Interpreted first, over a fast native engine.

**Principles** (in order of preference)
- **LG-PRN-1** Prefer modern syntax most programmers already know.
- **LG-PRN-2** Take philosophy and structure from older languages; take their syntax only where it adds real value.
- **LG-PRN-3** One obvious way to do each thing.
- **LG-PRN-4** Borrow only where the meaning carries over exactly; where AMP is new, let it look new.
- **LG-PRN-5** Names say what they hold.
- **LG-PRN-6** Types in PascalCase; values, functions and parameters in lowercase with underscores.

**Parties.** The owner. *Not signed.*

---

## Goals in detail

**LG-GOL-1 · Clear.** A reader should be able to read a script from top to bottom and know what it does, what it asks
the substrate, and what it will do with the answer, without running it and without consulting other files for hidden
meaning. Clarity is AMP's character, not a style preference: AMP's whole case rests on being trustworthy, and code that
can't be read can't be trusted. *Met when:* a reader new to a script can explain what each line does. *Not to be confused
with* brevity: a longer script that can be read is better than a shorter one that can't.

**LG-GOL-2 · Explicit.** Nothing a reader needs to know is left for them to infer: not the type of a value, not whether a
line can change the substrate, not which volume a function works on, not where a volume came from. Where other languages
allow something to be left out because a tool could work it out, AMP writes it down. The reason is the same as for
clarity, and also practical: much AMP code may be written by AI agents, and explicitness is what lets a person review it
and lets the interpreter catch mistakes before anything runs. *Not to be confused with* verbosity for its own sake: what
is written must carry information.

**LG-GOL-3 · Expresses AMP.** The language must be able to say everything AMP is for: create volumes and encoders,
declare structure that must hold, teach it from sources, let parts of it keep learning, ask it questions, and act on
the results, including their heat and ties. A language that needs workarounds (outside scripts, hand-edited structure)
for any of these has failed this goal. *Met when:* each of those can be written directly, as an ordinary part of a
program.

**LG-GOL-4 · Recognisable.** A programmer who knows a modern language (Rust, TypeScript, Kotlin, Swift and the like)
should be able to read an AMP script on first sight and follow its shape: where things are declared, where functions
begin and end, what calls what. What is genuinely new in AMP (volumes, encodings, results, heat) should be the only
unfamiliar part. *Not to be confused with* copying a particular language: AMP borrows conventions, not identity.

## Optimizations in detail

**LG-OPZ-1 · Simplicity.** Every construct must earn its place: it should give a lot of value, and it should not create
trade-offs that cause problems elsewhere. Before adding a construct, ask whether an existing one already does the job,
and whether it can be written as a function in AMP instead of built into the language. Measured as the number of
constructs a reader must learn to read any AMP program. *Trades against* LG-OPZ-3, when a familiar construct from another
language would add something AMP doesn't need.

**LG-OPZ-2 · Reviewability.** A script should be easy to check by someone who didn't write it: a colleague, an auditor, or
a person reviewing an agent's work. Types, effects and names should make mistakes stand out. Measured, roughly, as how
long it takes a reviewer to be confident a script does what it claims. *Supported by* LG-CON-1, LG-CON-2 and LG-PRN-5.

**LG-OPZ-3 · Familiarity.** Where AMP's meaning matches a modern convention, use that convention, so that what people
already know transfers. Comments, braces, function syntax, type annotations, tests and pipelines all follow what most
programmers recognise. *Gives way to* LG-OPZ-1 and to LG-PRN-4: familiarity never justifies a construct AMP doesn't need,
nor a familiar form whose meaning doesn't match.

## Constraints in detail

**LG-CON-1 · Static types, written out everywhere.** *Rule.* Every variable, parameter and return value has its type
written next to it. Nothing is inferred, even where a tool could infer it.

```
let digits: Volume = Volume(size: 64, density: 2% to 10%)
let first_digit: CellSet[digits] = digits{12}
```

The types established so far are `Encoder`, `Encoding`, `Volume`, `CellSet[V]`, `Assembly[V]`, `Heat[V]`, `HeatModel` and `Result[V]`,
with `Int`, `Ratio`, `Bool`, `Text` and `List[...]` underneath. *Why:* LG-GOL-2 and LG-OPZ-2; and because a state passed to the wrong volume, or a
result treated as a state, is the kind of mistake that is easy to make and hard to see. *If violated:* readers must
guess what values are, and the interpreter can no longer catch mistakes before running.

**LG-CON-2 · The substrate changes only where it is marked.** *Rule.* Only writing structure changes the substrate,
and every learning procedure is built on writing (LG-CAP-9). Any function that writes, or calls a function that writes,
must show it in its signature.
Everything unmarked can only read. A function that only asks questions can be called anywhere, in any order, any number
of times, and the substrate is exactly as it was afterwards. *The marker's spelling is still open:* the proposal follows
Rust, marking the parameter whose volume a function changes as `mut`.
*Why:* the system contract's rule that examination never feeds back into learning, made checkable in the code itself;
and it lets read-only questions run safely side by side. *If violated:* a question could quietly teach the substrate
something, results would depend on the order in which things were asked, and tests would stop meaning anything.

**LG-CON-3 · A result can't be ignored, and heat is never dropped.** *Rule.* Every result must be used: stored, returned,
passed on, or examined. Discarding one silently is an error. When a function builds its answer from several results,
the heat and ties of every one of them carry through into what it returns; no operation may hand back less than it was
given. A function that has examined some heat and dealt with it deliberately (for example by asking a person) may say so,
but must do it explicitly. *Not to be confused with* errors: heat is a normal part of a valid result, while an error is a
failure such as a missing file, a broken contract on a function, or an index outside a volume. *Why:* AMP's honesty
depends on uncertainty reaching whoever acts on the answer. *If violated:* a confident-looking final answer can hide an
uncertain step in the middle.

**LG-CON-4 · Values are immutable.** *Rule.* Once made, a value never changes. States, encodings and results stay as they
were created; operations produce new values rather than altering old ones.

```
let first_digit: CellSet[digits] = digits{12}
let with_operator: CellSet[digits] = first_digit + digits{40}   // first_digit is unchanged
```

The substrate's own structure is governed by the system contract (structure is only ever added, by writing); this
rule governs the values a program holds. *Why:* immutable values can be shared, compared, replayed and reasoned about.
*If violated:* a value seen in one place could differ from the same value seen later, and traces stop being trustworthy.

**LG-CON-5 · Nothing hidden.** *Rule.* What a reader sees is what runs. No hidden control flow (nothing runs that the
script doesn't show), no hidden volumes (every volume is created where the script says), no hidden learning (LG-CON-2), and
no hidden clean-up: a temporary volume is dropped where the script says it is dropped.

```
let scratch: Volume = Volume(size: 16, density: 5%)
defer scratch.drop()
```

*Why:* LG-GOL-1 and LG-GOL-2. *If violated:* the behaviour of a script can't be understood by reading it, which defeats
the point of AMP.

**LG-CON-6 · Deterministic.** *Rule.* The same script, given the same input and the same version of the substrate, always
produces the same results, including the same heat and the same ties. Nothing is decided by chance: where two answers
are equally supported, the tie is held and reported, never broken at random. *Why:* tests must mean something;
explanations must be reproducible; and a fast run can be explained later by replaying it exactly. *If violated:* the same
question could give different answers, tests would flicker, and "why did it do that?" could have no fixed answer.

**LG-CON-7 · Every loop that might not end has a limit.** *Rule.* Any repetition that might not stop by itself (a flow
that runs moment by moment until it settles, a recursive function, a search) declares an upper limit, and reaching the
limit is reported in the result. The limit is a safeguard, not a way of steering the answer. *Why:* a program must always
finish, and a run that hit its limit is itself important information. *If violated:* a program can hang, and nobody can
say how long anything will take.

**LG-CON-8 · Volumes and encoders are independent.** *Rule.* A volume knows nothing about encoders, and an encoder knows
nothing about volumes. An encoder returns encodings, which belong to no volume; a volume turns an encoding into one of its
own cell sets when asked.

```
let symbols: Encoder = Encoder(split: "character", cells: 1)
let sum_encoding: List[Encoding] = symbols.encode("3+4")
let digits: Volume = Volume(size: 64, density: 2% to 10%)
let first_symbol: CellSet[digits] = digits{sum_encoding[1]}
```

The same encoding can be used with any number of volumes, or with none. *Why:* each part stays simple and general, and
encoders (the boundary with the world) can be swapped without touching the substrate. *If violated:* volumes become tied to one
kind of input, and the engine stops being general.

**LG-CON-9 · The engine's implementation language has no influence on AMP's syntax.** *Rule.* The engine may be written
in Go today and in another language tomorrow. Nothing about AMP's syntax, naming or conventions follows from that
choice. *Why:* AMP is a different kind of language from whatever it is built in, and its shape should come from what it is
for. *If violated:* the language inherits accidents of its first implementation.

**LG-CON-12 · No floating point, unless one day explicitly opted into.** *Rule.* AMP's numbers are `Int` (whole
numbers) and `Ratio` (exact fractions; a percentage such as `2%` is the ratio 1/50). There are no floating-point
numbers. If they are ever genuinely needed, they arrive as an explicit opt-in, never as a default. *Why:* floating-point
results can differ slightly between machines and between an interpreter and a compiler, which would break LG-CON-6
(determinism) and the promise that every way of running AMP gives the same results. *If violated:* the same program could
give different answers on different machines, and tests would stop being trustworthy.

**LG-CON-13 · Heat models are built in. Programs cannot define their own.** *Rule.* Every heat model is part of the
language, implemented and optimised in the engine. A program chooses among them; it cannot write a custom one. *Why:*
custom heat models would make programs and substrates hard to compare and exchange, and would run slowly in the engine's
innermost loop. With built-in heat models only, a program depends on nothing beyond the language version, which can be
managed with ordinary practices for forwards and backwards compatibility. *If violated:* interoperability is lost, and
"heat" stops meaning the same thing from one program to the next.

**LG-CON-10 · No implicit types.** *Conflict* with LG-CON-1 and LG-GOL-2. Type inference is common and convenient in
modern languages, and is deliberately left out.

**LG-CON-11 · No global state reached for unseen.** *Conflict* with LG-CON-5. A function works only on the volumes it is
given as parameters or creates itself.

```
fn complete_sum(digits: Volume, sum_cue: CellSet[digits]) -> Result[digits] { ... }
```

## Capabilities in detail

**LG-CAP-1 · Volumes are values, created anywhere.** A volume is created by calling its constructor, `Volume(...)`, and can be stored in a
variable like any other value: at the top of a script for a lasting volume, or inside a function for a temporary one that
is dropped explicitly. One form serves both. A volume declares its size and its density; density may be a range within
which it is allowed to move (what moves it is not yet decided).

**LG-CAP-2 · Cells addressed by index or by label.** Inside braces, a bare number is an index into the volume and quoted
text is a label from an encoder: `digits{12}` is cell 12 of digits; `symbols{"3"}` is the encoding symbols gave to "3",
which a volume can turn into a state. The quotes keep the two from ever being confused, which matters in arithmetic,
where "12" is a perfectly good label. Indexes are checked against the volume's size: an index outside it is an error.

**LG-CAP-3 · Encoders return encodings; volumes turn encodings into cell sets.** An encoding carries three things: its
indexes, its label, and its source (the input and position it came from). The source is where provenance begins: the
system contract requires every piece of structure to keep its source, and only the encoder knows it. An encoder also
states how wide its output is, so a volume too small for it is caught before anything runs.

**LG-CAP-4 · A cell set's type carries its volume.** A cell set of digits has the type `CellSet[digits]`, so passing it
where another volume's cell set is expected is caught as a type error. Results carry their volume the same way:
`Result[digits]`.

**LG-CAP-5 · A small core and a standard library.** The engine provides a small set of primitives (so far `complete`,
`touch`, the cell set operators and `sample`, with others under discussion). Everything else useful is written in AMP
itself, as functions, and shipped as a standard library. If something useful can't be written that way, that is the sign
it may need to be a primitive. This keeps the engine small and the explanations uniform.

**LG-CAP-6 · Operators on cell sets.** Union, intersection, difference and symmetric difference are written as operators
(proposed: `+`, `&`, `-`, `^`, with `==` and `in`), not function calls, with one way to write each. They work on cell sets
of the same volume and return new cell sets. They are plain set operations: they don't consult the substrate or learn
anything.

**LG-CAP-7 · Tests built into the language.** Tests are written in AMP, next to the code they check, and run with one
command. A test gives an input and states what the result must contain, including where heat and ties must or must not
appear. When new knowledge outcompetes old, a test breaks, and that is where the engineer looks.

```
test "3+4 completes to 7" {
   let completion: Result[digits] = complete_sum(digits, "3+4=")
   expect completion.candidates contains digits{symbols{"7"}}
}
```

**LG-CAP-8 · Interpreted first, over a fast native engine.** AMP runs through an interpreter, which defines what the
language means and makes stepping through, inspecting and asking "why" natural. Speed comes from the engine underneath,
not from compiling scripts. Compiling frozen memories, or compact forms for small devices, may come later; if it does, the
compiled form must give exactly the same results as the interpreter, and every test runs on both.

**LG-CAP-9 · Learning written in AMP, from primitives.** The language has no built-in learning method. It provides the
primitives every learning method is built from (reading a volume, completing, touching, cell set operators, sampling,
writing), and learning procedures are ordinary functions written from them. The right way for associative memory to
learn is still a research question, and the language should make every candidate expressible rather than bet on one.
Structure formed by any procedure is ordinary structure with sources, so substrates stay comparable and exchangeable.
The language keeps the balance between learnt and written structure visible: every assembly records which procedure
formed it and from what, and is classed as learnt, written or mixed (the mechanism is in progress in the specification).

## Principles in detail

**LG-PRN-1 · Prefer modern syntax most programmers already know.** Where there is a choice of form, choose the one most
programmers today will recognise: `//` comments, braces for blocks, `fn` for functions, `name: type` annotations,
`|>` for pipelines. *Gives way:* to LG-PRN-4, when the familiar form would mean something different in AMP.

**LG-PRN-2 · Take philosophy and structure from older languages; take their syntax only where it adds real value.**
Older, principled languages have much to teach: Prolog and Datalog about asking questions that say what you want and
recursion that settles; Ada and SPARK about explicit declarations and contracts on functions; Lustre about moments and
flow; Lisp about a small core. AMP takes those lessons, but writes them in modern form unless the older syntax is
clearly better. *Gives way:* when an older form is clearly the best expression of something AMP needs.

**LG-PRN-3 · One obvious way to do each thing.** When two constructs would do the same job, keep one. Two ways of
writing the same thing make code harder to read and review, and force every reader to learn both. *Gives way:* never to
convenience alone; only when two forms genuinely mean different things.

**LG-PRN-4 · Borrow only where the meaning carries over exactly; where AMP is new, let it look new.** A borrowed word or
form brings its meaning with it. If AMP's meaning differs, the borrowing misleads. So AMP's own ideas (volumes,
encodings, results, heat, ties, assemblies) keep their own forms: braces for sets of cells, quotes for labels, angle
brackets for assemblies. That is also why types use square brackets (`CellSet[digits]`), leaving angle brackets to
assemblies alone.

**LG-PRN-5 · Names say what they hold.** Variables, parameters and functions have names that say what they are:
`sum_encoding`, not `e`; `first_digit`, not `s`; `complete_sum`, not `cs`. No single letters and no abbreviations.
Examples in documentation follow this rule above all, because examples become the idiom. Tooling may warn on names that
break it. *Why:* LG-GOL-1 and LG-OPZ-2; in a language built on clarity, unclear names are a contradiction.

**LG-PRN-6 · Types in PascalCase; values, functions and parameters in lowercase with underscores.** `Volume`, `CellSet`,
`HeatModel`; `fruit`, `apple_cue`, `sized_volume`. This is the convention of Rust, Swift, Kotlin, TypeScript and most
modern languages, so it transfers directly. A volume's name is a value and stays lowercase even inside a type:
`CellSet[fruit]`.

---

## Open, to be decided

- The spelling of the marker for code that changes the substrate (LG-CON-2); `mut` on the parameter is proposed.
- What moves a volume's density within its range: the engine's own dynamics, scripts within limits, or both.
- How a volume's activity unfolds over a sequence (feeding a list of encodings moment by moment), and whether scripts can
  read that activity.
- The full set of primitives beyond `complete`, `touch` and the set operations.
- The syntax for ranges of indexes.
- The full detail of each topic is tracked in the language specification (`language-specification/`).
