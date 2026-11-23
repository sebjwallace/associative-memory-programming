# Contract · The system · proposed

*Drafted by the assistant from the owner's words and from the Anneal system contract (anneal-machine, CTR-1),
generalised for Associative Memory Programming as a discipline rather than one theory of general intelligence. Not in
force until the owner signs. Clauses marked **draft** are proposed but not yet confirmed. This is meant to start broad
and become more specific over time.*

This contract describes the essential shape of AMP: what it is for, what it must and must not be, and what to prefer
when choices are open, whoever builds it and however. It describes a target, not today's code.

## How to read it

- **Goals** say where to go. A goal is reached once and stays reached. They are in order of priority.
- **Optimizations** are directions, never finished, balanced against each other. They are in order of priority: when
  two pull apart, the higher one wins, and a large loss to a higher one is never bought with a small gain to a lower one.
- **Constraints** say what is off the table. **Limits** are impossible whatever anyone chooses. **Rules** are chosen to
  protect the goals and don't give way. **Conflicts** are possible, but would break another clause.
- **Capabilities** say what is on the table: options that make the goals easier to reach. Nothing must use them, but a
  rebuild that forgets one will fall short.
- **Principles** say what to prefer when several valid options are open. Each gives way to something.

The test for where a clause belongs: if it may never give way, it is a constraint; if it is something the system can
use, a capability; if it is a direction, an optimization; if it is a preference, a principle.

Every clause has a code. A code is a name, not a position: it stays with its clause if the clause moves.

**Two levels.** AMP has an **engine** (general, the same for every use) and **programs** (specific, built by people on
the engine). Several clauses depend on keeping the two apart: the engine holds no task-specific rules, while a program
may declare whatever it needs, openly.

---

## Definitions

Words are agreed deliberately. Where a name is still open, it is marked.

- **DEF-1 Engine.** What performs the operations and holds the memory. General: the same for every program.
- **DEF-2 Memory.** Everything the engine holds: what it knows and what is happening now, together. Never means RAM.
- **DEF-3 Program.** A memory shaped for a purpose: its volumes and how they are wired, its declared structure, what it
  was taught, which parts may keep learning, and its rules for output.
- **DEF-4 Cell.** The smallest unit. Active or not.
- **DEF-5 Volume.** A container of cells, and of other volumes. A volume has behaviour of its own, such as how many of
  its cells may be active at once and so what competes inside it. *(Replaces population and community.)*
- **DEF-6 Connection.** A directed link from one cell to another, present or not. *(Name open: replaces "bond".)*
- **DEF-7 Gate.** A group of connections arriving at one cell, with a threshold: the cell can turn on when enough of the
  group is active.
- **DEF-8 Assembly.** A group of cells whose connections loop back on each other, so any sufficient part brings back
  the rest. What AMP recognises and recalls.
- **DEF-9 Transition.** A chain of connections pointing forwards, carrying activity on to what comes next. What AMP
  follows as a sequence or procedure.
- **DEF-10 Activity.** Which cells are active at a moment. Not necessarily something that has happened before or will
  again. *(Name open: "activity" or "active set".)*
- **DEF-11 Heat.** What is left incomplete: activity that nothing explains, a gap, a misfit, rivals that can't both
  hold. Energy that can't flow.
- **DEF-12 invoke.** The reading operation: input arrives, the memory completes, rivals compete, and what can't be
  explained is left as heat.
- **DEF-13 anneal.** The learning operation: new structure forms to resolve heat. Composition, abstraction and
  decomposition are shapes it takes.
- **DEF-14 Loaded and stored.** Where structure physically lives: loaded is in RAM, stored is on disk. Heat words
  (warm, cold) are kept for heat only.
- **DEF-15 Source.** Where a piece of structure came from: what was received, what was declared, or what the engine
  formed itself, with a pointer back to it.

---

## The sheet

**Goals** (in order of priority)
- **GOL-1** Programmable: a memory can be shaped by declaring structure, by teaching it from examples, and by letting it
  grow on the job, all mixed in one program.
- **GOL-2** Learns unsupervised and online: placed in front of input, it resolves the heat in it, with no labels,
  training phase or teacher required.
- **GOL-3** Useful on the job: it does useful work from its first exposures and improves while it works.
- **GOL-4** Explains itself: for anything it does, it can give the exact cause in its own terms.
- **GOL-5** Understandable: what it knows can be explored directly, through tools that read its structure.
- **GOL-6** *(draft)* Composable: volumes nest and connect with no new mechanism; a memory can be saved, shared and
  built upon.
- **GOL-7** *(draft)* Acts: a program can drive outputs and carry out procedures, not only recognise and recall.

**Optimizations** (in order of priority)
- **OPZ-1** Heat: resolve more of what it receives, never by masking it.
- **OPZ-2** Information: learn as much from far less information than today's AI needs.
- **OPZ-3** Minimality: the fewest constructs that explain the most.
- **OPZ-4** Compute: fewer resources (time, memory, power) for the same work, on ordinary hardware.
- **OPZ-5** Scale: the work of reading and recalling grows with what is active, not with what is stored.
- **OPZ-6** *(draft)* Explanations: as short and readable as possible, from one gate to a whole run.
- **OPZ-7** *(draft)* Understanding: as few steps as possible from anything it knows to its neighbours and its sources.

**Constraints**
- *Limits*
- **CON-1** It can't learn what isn't in what it receives or is given.
- **CON-2** It can't try every explanation: search is always partial.
- **CON-3** Memory is finite and good enough, not exact: exact records live outside it, linked.
- **CON-4** Evidence alone can't settle a true tie: only more evidence can.
- *Rules*
- **CON-5** Resolve, don't mask. *Hard.*
- **CON-6** Binary structure: no learnt strengths or weights; reinforcement is more structure. *Hard.*
- **CON-7** Nothing breaks: learning only adds structure; what loses is stored, not erased. *Hard.*
- **CON-8** Nothing happens without a recorded cause. *Hard.*
- **CON-9** Every piece of structure keeps its source; what is inferred or imagined is never recorded as received.
  *Hard.*
- **CON-10** Don't guess: a true tie is held open. *Hard.*
- **CON-11** A general engine: nothing in the engine is written for one task or one kind of input. *Hard.*
- **CON-12** No gradients, backpropagation or optimiser: learning is forming structure. *Hard.*
- **CON-13** Examination never feeds back into learning. *Hard.*
- **CON-14** A program's purposes are declared: what it is for, and what must never bend, is stated openly. *Hard.*
- **CON-15** Sparse and event-driven: work happens only where something is active or changing. *Hard.*
- **CON-16** Runs on ordinary hardware: no specialised hardware required. *Hard.*
- *Conflicts*
- **CON-17** No perfect memory (breaks CON-3, OPZ-4).
- **CON-18** No exhaustive search for the best answer (breaks OPZ-4; see CON-2).
- **CON-19** No supervised training signal as the means of learning (breaks GOL-2, CON-12).

**Capabilities**
- *Core*
- **CAP-1** Completion: a few active pieces bring back the whole assembly.
- **CAP-2** Competition: rival explanations contend, and the better supported wins.
- **CAP-3** Sparse distributed representation: a thing is a small set of cells; alike means sharing cells.
- **CAP-4** Learning by comparing: what two things share becomes a part; what differs is what's left.
- **CAP-5** Binding what happens together: what is active together, and unexplained, can form one assembly.
- **CAP-6** Transitions: activity carried forward, giving sequence, order and procedure.
- *Supporting*
- **CAP-7** Holding: an assembly stays active until something changes it, steering what comes next.
- **CAP-8** Composition, abstraction and decomposition: assemblies of assemblies, shared overlaps, and parts taken out.
- **CAP-9** Heat as a valve: effort opens only where something doesn't fit.
- **CAP-10** Not knowing is a reason to look: a held tie becomes a cue for more evidence.
- **CAP-11** Rest: heavy work done when nothing is coming in.
- **CAP-12** Loaded and stored by demand: what is relevant is in RAM, the rest on disk, primed back when needed.
- **CAP-13** Declared fixed structure: assemblies and transitions written by hand that always win.
- **CAP-14** *(draft)* Building on other memories: starting a program from a memory someone else built.

**Principles** (in order of preference)
- **PRN-1** Prefer the deeper explanation to a new mechanism.
- **PRN-2** Prefer the same mechanism with different settings to a different mechanism.
- **PRN-3** Prefer resolving a misfit to building around it.
- **PRN-4** Prefer more structure to stronger structure.
- **PRN-5** Let heat decide where effort goes.
- **PRN-6** Settle locally first.
- **PRN-7** Prefer what was received to what was inferred.
- **PRN-8** *(draft)* Where a person must understand, prefer showing the gap to filling it.

**Parties.** The owner. *Not signed.*

---

## Details

### Goals in detail

**GOL-1 · Programmable.** The goal that makes AMP a discipline rather than one system. An engineer can shape a memory
in three ways, freely mixed: **declare** structure by hand (the rules that must hold, the skeleton of a procedure),
**teach** it from examples (invoke and anneal on chosen input, then fix what was learnt), and **grow** it on the job
(leave chosen parts free to keep learning). *Met when:* one program uses all three, and the result can be tested and
explained like any other. *Not to be confused with* "learns only from what it's given": declared structure is a first
class way to program, not a shortcut around learning (CON-14 keeps it honest).

**GOL-2 · Learns unsupervised and online.** Nobody tells it what anything is or what the right answer is. What it learns
comes from resolving the heat in what it receives (CON-5). Teaching by example is still unsupervised in this sense:
examples are input, not answers to be graded. *Met when:* the same engine, unchanged, learns from several different
kinds of input. *Not to be confused with* learning from an unlabelled training set: there needn't be a training set at
all.

**GOL-3 · Useful on the job.** There is no phase where it learns and a later phase where it is used. Using it is how it
learns, where the program allows. *Met when:* from its first exposures it already recognises, completes or predicts
something useful, and keeps improving. *Not to be confused with* "needs no learning".

**GOL-4 · Explains itself.** Any decision can be answered with its exact cause: a gate's connections against what was
active, an assembly's support against its rival's, the heat a new assembly resolved, what loaded or stored something.
Because structure is binary and made of sets, the counts it decides by are the explanation. *Gives:* the means to
develop and debug it (AMX), trust, and discoverable tampering. *Not a claim of:* simplicity at scale, or correctness.

**GOL-5 · Understandable.** Distinct from GOL-4: that answers *why it did something*; this answers *what it knows*.
What it has learnt (assemblies, how they group, the sequences they appear in, and the sources that formed them) can be
navigated directly through tools that read the structure, not through text it generates about itself. An open box.
*Not a claim of:* ease at scale, or correctness.

**GOL-6 · Composable** *(draft)*. Volumes inside volumes, connected to each other, are the same engine again (PRN-2). A
memory can be saved, shared and used as the starting point of another program, so knowledge can be layered: general
first, then a domain, then a team's own. *Open:* the unit that is saved, shared and imported, and its name.

**GOL-7 · Acts** *(draft)*. A program can drive outputs (commands, actuators, messages) and carry out procedures as
chains of transitions, holding where it is in them. Whether a program chooses its own actions from its own heat, as the
Anneal research explores, is left to that research; this goal asks only that acting be possible.

### Optimizations in detail

**OPZ-1 · Heat.** Explain more of what it receives, more completely, with misfits genuinely resolved, never covered
(CON-5). Heat that won't settle is reported, not hidden. *Note:* heat measures coherence, not truth. Something false that
hangs together produces none, so no clause may present "settled" as "true".

**OPZ-2 · Information.** Measured as how much it must receive to learn a thing. The reason it compares rather than
averages (CAP-4): what two things share can be seen from two examples. *Trades against* OPZ-3 and OPZ-4, since learning
from one exposure keeps structure sooner.

**OPZ-3 · Minimality.** Applies to the design of the engine: the fewest mechanisms, rules and kinds of structure from
which everything else follows, as one simple construct explains so much in a Turing machine. A new capability that
needs a new mechanism is a cost (PRN-1). Constructs are the measure, not lines of code. *Trades against* OPZ-4.

**OPZ-4 · Compute.** Time, memory and power per thing learnt or answered, on ordinary hardware (CON-16).

**OPZ-5 · Scale.** The work of reading and recalling should follow what is active, not what is stored: millions of
assemblies, and it still runs fast. Supported by CON-15 and CAP-12.

**OPZ-6 · Explanations** *(draft)*. One gate's reason is short by nature; the work is at scale, where many simple parts
interact. Measured as how long and how readable the answer to "why" is, for one moment and for a whole run. *Trades
against* OPZ-4 (the record costs memory) and OPZ-3 (summarising tools are more constructs).

**OPZ-7 · Understanding** *(draft)*. Large memories need folding: many small assemblies gathered into the few that
matter, built from the structure itself. Measured as steps from anything to its neighbours and sources.

### Constraints in detail

**CON-1 · It can't learn what isn't there.** *Limit.* What it learns is bounded by what it receives or is given. *If
ignored:* knowledge it had no way to get gets supplied quietly by hand.

**CON-2 · It can't try every explanation.** *Limit.* Possible explanations explode, so search is always partial. *If
ignored:* it hangs, or shortcuts creep in.

**CON-3 · Memory is good enough, not exact.** *Limit.* Exact records (recordings, documents, figures) live outside the
memory, and structure links to them. *If ignored:* structure grows without bound, and compute with it.

**CON-4 · Evidence alone can't settle a true tie.** *Limit.* Only more evidence can: looking, asking or acting. *If
ignored:* it guesses, breaking CON-10.

**CON-5 · Resolve, don't mask.** *Rule.* Heat may only fall because a misfit is actually resolved, never because its
measure is covered or a patch is built around it. *If violated:* heat falls while understanding doesn't; the system
learns to cheat its own measure and can't be trusted.

**CON-6 · Binary structure.** *Rule.* A cell is active or not; a connection exists or not. There are no learnt
strengths, weights or activation levels. Reinforcement means more structure, not stronger structure. *Note:* counts that
come from the structure itself (how many of a gate's connections are active) are the basis of every decision and are
allowed; the rule forbids stored strengths, not counting. *If violated:* tuning creeps in, explanations stop being
counts, and memory can blur as it fills.

**CON-7 · Nothing breaks.** *Rule.* Learning only adds structure. Assemblies and connections, once formed, are not
edited or removed by learning. Being wrong means new structure forms and outcompetes the old. What stops being relevant
is stored, still connected and still traceable. Deletion happens only as a storage policy or at an owner's request (for
example, removing what came from one source), never as part of learning. *If violated:* history is lost, mistakes can't
be traced, and memories can't be compared across versions.

**CON-8 · Nothing happens without a recorded cause.** *Rule.* Every change to structure (forming, loading, storing) and
every activation has a cause that can be stated in AMP, and changes are kept in a record with their causes. *Checkable:*
any run can be replayed from its record, and every entry names its cause. *If violated:* it can't be developed by
examining it, mistakes and tampering can't be traced, and GOL-4 is lost.

**CON-9 · Sources kept; inferred never recorded as received.** *Rule.* Every piece of structure records whether it came
from input, from a declaration, or from the engine's own forming, with a pointer back. What the engine joins, imagines
or infers is never recorded as something it received. *If violated:* made-up content hardens into fact, guesses compound,
unlearning becomes impossible, and ownership can't be honoured.

**CON-10 · Don't guess.** *Rule.* Where the evidence fits two explanations equally, neither is taken; the tie is held
open and reported. *If violated:* invented content is stored, recalled as fact, and compounds.

**CON-11 · A general engine.** *Rule.* No rule, filter or mechanism in the engine is written for one task or one kind of
input. Fixed architecture is allowed because it is the same everywhere. Task-specific knowledge belongs in programs, as
declared structure (CON-14). *If violated:* the engine works on its demonstration and piles up special cases elsewhere,
the opposite of OPZ-3.

**CON-12 · No gradients, backpropagation or optimiser.** *Rule.* Learning is the forming of structure in response to
heat. *If violated:* it becomes another kind of trained model, and GOL-2, GOL-4 and OPZ-2 go with it.

**CON-13 · Examination never feeds back.** *Rule.* Tools that examine the memory (AMX, AMT) only read. Names given while
examining are for reading only. *If violated:* results stop meaning anything, because the examiner has become part of
what is being examined.

**CON-14 · Purposes are declared.** *Rule.* What a program is for (its outputs, the conditions it holds towards, the
structure that must always win) is declared by its author, openly, and marked as declared (CON-9). The engine never sets
its own purposes. *If violated:* a system that chooses its own targets can meet them by choosing easy ones, which is
masking (CON-5), and what it is for becomes invisible.

**CON-15 · Sparse and event-driven.** *Rule.* Work is done only where something is active or has just changed; what stays
the same is not recomputed; nothing scans or scores the whole memory at once. *If violated:* cost grows with everything
held rather than with what is happening, breaking OPZ-4 and OPZ-5, and designs drift towards needing special hardware.

**CON-16 · Ordinary hardware.** *Rule.* It runs on ordinary CPUs, down to small devices, with no GPU or other
specialised hardware required. Hardware built for it later is welcome; needing it is not. *If violated:* OPZ-4 quietly
becomes "buy faster hardware".

**CON-17 · No perfect memory.** *Conflict* with CON-3 and OPZ-4.

**CON-18 · No exhaustive search for the best answer.** *Conflict* with OPZ-4; see CON-2.

**CON-19 · No supervised training signal as the means of learning.** *Conflict* with GOL-2 and CON-12. Declaring
structure (GOL-1) is not a training signal: it is programming, and is marked as such.

### Capabilities in detail

**CAP-1 · Completion.** *Gives:* content-addressable recall. A fragment brings back the whole; a missing part is filled
in; recognition from partial, noisy input. *Serves:* GOL-2, GOL-3, OPZ-2. *Costs:* a cue that fits several assemblies
equally recalls none (CON-10), so sometimes more evidence is needed.

**CAP-2 · Competition.** *Gives:* rival explanations contend for the same cells, and the one with more support wins. One
more supporting cell is enough. It is how AMP rejects what doesn't fit, and how a volume with room for one active cell
acts as a variable. *Serves:* GOL-1, GOL-7, CON-10. *Costs:* ties must be held, not broken arbitrarily; and because more
structure means more support, a source that supplies more input can outcompete one that supplies less. Where that
matters, how support is counted (per item, per source, per party) is a program's declared choice (CON-14).

**CAP-3 · Sparse distributed representation.** *Gives:* a thing is a small set of cells; similarity is shared cells, with
no separate rule; many things can be active at once. Counting shared cells suits ordinary CPUs. *Serves:* OPZ-4, OPZ-5,
CON-16. *Costs:* how the world is encoded into cells is a design choice at the edge of every program.

**CAP-4 · Learning by comparing.** *Gives:* what two things share becomes a part; what differs is what's left. Fast and
exact where averaging is slow and blurred. *Serves:* OPZ-2, OPZ-3. *Costs:* comparing is work, best done at rest
(CAP-11).

**CAP-5 · Binding what happens together.** *Gives:* things active together and unexplained can form one assembly,
Hebbian in spirit but with no strengthening: repetition matters only as more structure (PRN-4). *Serves:* GOL-2, OPZ-2.

**CAP-6 · Transitions.** *Gives:* sequence, order and procedure; prediction of what comes next; chained steps that, with
holding, give loops, counting and subroutines. *Serves:* GOL-7, GOL-1.

**CAP-7 · Holding.** *Gives:* an assembly that stays active until something changes it, so context persists through gaps
and noise and steers what comes next. *Serves:* GOL-7, OPZ-2. *Costs:* what is held takes part in everything; letting go
should come from change, not a timer.

**CAP-8 · Composition, abstraction and decomposition.** *Gives:* assemblies built from assemblies; what several share
becoming its own assembly; parts taken out of wholes. The set words union, intersection and difference describe them.
*Serves:* OPZ-2, OPZ-3, GOL-5.

**CAP-9 · Heat as a valve.** *Gives:* effort spent only where something doesn't fit. *Serves:* OPZ-4, PRN-5.

**CAP-10 · Not knowing is a reason to look.** *Gives:* a held tie becomes a cue for more evidence: a question for a
person, a look elsewhere, an action. *Serves:* CON-10, GOL-7.

**CAP-11 · Rest.** *Gives:* heavy work (comparing, composing, replaying) done when nothing is coming in, so reading stays
quick. *Serves:* GOL-3, OPZ-4. *Costs:* the memory changes while it rests; programs should schedule rest deliberately.

**CAP-12 · Loaded and stored by demand.** *Gives:* what is relevant is loaded; what loses or goes unused is stored, still
connected, and primed back into RAM by activity that needs it. *Serves:* OPZ-5, CON-7.

**CAP-13 · Declared fixed structure.** *Gives:* assemblies and transitions written by hand, marked as declared, that
learning can never outcompete: guardrails as structure, provably present. Declared structure can also state what
*should* be present, so that an absence becomes heat: without it, nothing points at what is missing, and its absence is
silent. *Serves:* GOL-1, CON-14, OPZ-1. *Costs:* declared structure is the author's responsibility; it is visible so it
can be questioned.

**CAP-14 · Building on other memories** *(draft)*. *Gives:* a program that starts from a memory someone else built
(general language, common sounds, a field's vocabulary) and layers its own on top. *Serves:* OPZ-2, GOL-6. *Costs:*
inherited structure carries its sources and its mistakes; it must stay examinable.

### Principles in detail

**PRN-1 · Prefer the deeper explanation to a new mechanism.** When a new ability seems to need a new part, first look for
something deeper that explains the new and the old together. *Why:* OPZ-3. *Gives way:* when the evidence shows there is
none, and then the new mechanism is declared.

**PRN-2 · Prefer the same mechanism with different settings to a different mechanism.** A new volume, level or kind of
input should be the engine again. *Why:* OPZ-3, CON-11. *Gives way:* when the old mechanism genuinely can't do it, which
is also a reason to revisit PRN-1.

**PRN-3 · Prefer resolving a misfit to building around it.** A patch is a misfit hidden inside structure. When something
doesn't fit, find what actually resolves it. *Why:* CON-5. *Gives way:* never to a patch; only to holding the heat open
and reporting it.

**PRN-4 · Prefer more structure to stronger structure.** Reinforcement is more connections and more supporting context
around something, not a bigger number on it. *Why:* CON-6, GOL-4. *Gives way:* to OPZ-4 when structure grows without
paying its way, which storage (CAP-12) handles.

**PRN-5 · Let heat decide where effort goes.** Work where something doesn't fit, not everywhere just in case. *Why:*
OPZ-4, CAP-9. *Gives way:* to rest (CAP-11), when the whole needs reorganising.

**PRN-6 · Settle locally first.** Resolve heat as close to where it arises as possible; only what can't be settled there
spreads. *Why:* OPZ-4, and volumes settling each other without every part reacting to everything. *Gives way:* when
settling locally would mask the misfit (CON-5).

**PRN-7 · Prefer what was received to what was inferred.** When a memory of what happened and something worked out
disagree, trust what happened until new evidence says otherwise. *Why:* CON-9, trust. *Gives way:* to fresh evidence,
never to a better-sounding inference.

**PRN-8 · Where a person must understand, prefer showing the gap to filling it** *(draft)*. When the purpose of a
program is for someone to learn or decide, report what doesn't fit and where each part came from, rather than
completing it for them. *Why:* people at the helm; settling that happens only in the machine leaves the person where they
started. *Gives way:* when the program's declared purpose is to act (GOL-7), or when the person asks for the completion.

---

## What was carried over, changed or left out

From the Anneal system contract (CTR-1), for the record.

**Carried over, generalised:** unsupervised and online learning, useful on the job, explains itself, understandable;
heat, information, minimality, compute, scale, explanations and understanding as directions; the four limits; resolve
don't mask; recorded causes; don't guess; general; no backpropagation; set points declared from outside; sparse and
event-driven; ordinary CPUs; the core capabilities; the principles of deeper explanation, same mechanism, letting heat
lead, settling locally, and trusting what was lived.

**Changed:**
- *"Imagined is never stored as lived"* is widened into **keeping sources** (CON-9), which also serves ownership and
  unlearning.
- *"Set points from outside, declared"* becomes **purposes are declared** (CON-14), covering guardrails and outputs.
- *"Online, from nothing"* is relaxed: a program may start from declared or inherited structure (GOL-1, CAP-14), as long
  as that is marked.
- *"Cells carry no numbers"* is restated as **no learnt strengths or weights** (CON-6), allowing counts from structure,
  in line with the owner's plan to loosen the original wording.
- *"Cells and segments first"* becomes **sparse, event-driven, nothing scans the whole** (CON-15), so it doesn't conflict
  with assemblies being first-class.
- *"Prefer removing structure to adding it"* conflicted with nothing breaking. It becomes **prefer resolving a misfit to
  building around it** (PRN-3), which keeps its intent: no patches.

**Left out, as stale or specific to the old engine:**
- Energy as the cost of a whole description, the "one rule" that a change is kept only if that cost falls, and "one
  currency taken from the world": these belong to the retired core's pricing. Heat as incompletion replaces them.
- Thresholds from prices, the exact-records notebook (now legacy), and the two kinds of memory: specific mechanisms,
  not yet settled for AMP.
- Columns, segments, and other names from earlier designs.
- "Acts on its own heat" and "regions settle each other": these belong to the Anneal research into general
  intelligence. GOL-7 asks only that acting be possible.

## For the owner to decide

1. The names still open: the word for a connection (DEF-6) and for the cells active at a moment (DEF-10), and the unit
   that is saved and shared (GOL-6).
2. Whether "volume replaces population and community" (DEF-5) holds, and where a volume's behaviour (sparsity,
   competition) is declared.
3. The order of goals and optimizations as priorities. Proposed: programmable first, because that is what makes AMP a
   discipline; heat first among optimizations.
4. The drafts: GOL-6, GOL-7, OPZ-6, OPZ-7, CAP-14, PRN-8.
5. Whether deletion at an owner's request (CON-7) belongs here or in a separate contract about ownership and data.