# Vision

*Where Associative Memory Programming is heading, and why. This is a North Star and a premise, not a roadmap: most of
what follows is not built, and much of it still has to be proven. The aim is to make the idea concrete enough to build
towards, and honest enough to argue with.*

---

## The North Star

**Intelligence that is designed, programmed and examined, rather than trained by brute force.**

Software comes into existence today in one of two ways. It is **written, then run**: exact, predictable, and brittle
when the world gets messy. Or it is **trained, then deployed**: flexible, but hungry for data, expensive to run, and
closed to inspection.

AMP offers a third way: **grow it, read it, correct it.**

- **Grow it.** Declare the shape of a memory and the parts that must never bend, teach the rest by example, and let it
  keep learning on the job.
- **Read it.** Everything it knows is structure you can walk through. Everything it does has a reason you can trace.
- **Correct it.** A fix is an example or a declared piece of structure, not a retraining run. You can see exactly what
  changed, compare versions, and return to any earlier one.

If that works, associative memory becomes an engineering discipline: something people can build with, test, trust and
certify, the way they trust bridges and circuits, at every scale from a single sensor to an enterprise.

---

## The premise

Eight tenets came out of exploring AMP across many directions: different scales, different domains, different people.
They are the ideas that held up everywhere. Each still has to be proven in the engine; together they are what this
project is building.

### 1. You set the dial between hard and soft

Hand-written code is hard: exact, rigid, unable to keep up with the regularities and irregularities of real data. Deep
learning is soft: it absorbs the noise, but it can't be trusted, traced or corrected with any precision. Most
organisations, and most people, are stuck choosing between too hard and too soft.

AMP gives the engineer a dial. A program is shaped in three ways, freely mixed:

- **Declare** structure by hand: the rules that must never bend (regulations, safety limits, contract terms, hard facts),
  written as fixed structure that always wins. Guardrails become part of the program, and you can prove they are there
  by looking.
- **Teach** it from examples, sometimes by people who aren't programmers at all: a technician, a warden, an analyst, an
  elder.
- **Grow** it: leave chosen parts free to keep learning on the job.

Where the line between fixed and loose sits is a design decision, visible to everyone, not something buried in a model.

### 2. Heat is honest

In AMP, heat is whatever doesn't fit yet: a gap, a conflict, something unexplained. Where information fits together, it
settles and heat falls. Where it conflicts or has holes, the heat stays, and nothing smooths it over.

That makes AMP honest in a particular sense. It doesn't claim to know the truth. It is honest about **its own
coherence**: what fits, what doesn't, and what is missing. Give a language model two sides of a conflict and it tends to
blend them into smooth, plausible prose, and the seams disappear. AMP refuses to blend. The refusal is the honesty.

Every result carries this with it: what was completed, how well it fitted, any ties left open, and what was left
unexplained. The rest of a program, and the people using it, can act on that: ask a person, look elsewhere, or learn.

The limits of this honesty are part of the premise (see "Honesty and its limits" below): fitting is not the same as
being true, absence is silent unless something expects it, and volume is not the same as weight.

### 3. A glass box

Two kinds of openness, by design:

- **Explainable:** for anything it does, it can state the exact cause. Because structure is binary and made of sets, the
  counts it decided by are the explanation. Nothing is generated after the fact.
- **Understandable:** what it knows can be explored directly, as structure, through tools that read it. An open box, not a
  black box you have to question from outside.

Underneath both is **provenance**. Every piece of structure records where it came from: what it read, what it was told,
or what it worked out itself, with a pointer back. What it infers is never recorded as something it received. That is
what makes ownership, audit and unlearning possible.

### 4. Nothing breaks

Learning only adds structure. Being wrong doesn't erase anything: new structure forms beside the old and outcompetes it.
What stops being relevant is moved to disk, still connected and still traceable.

So a memory has a full history. You can rewind it to any moment and ask what it knew then. You can fork it, change one
piece of evidence, and compare. You can review what it learnt like a pull request: these assemblies formed, prompted by
these inputs, and now outcompete these. And it sidesteps one of machine learning's hardest problems: teaching a trained
model something new tends to damage what it already knew. AMP learns beside what it knows.

### 5. Learns on the job, from little, cheaply

There is no separate training phase: using it is how it learns, where the program allows. It learns by comparing and
composing rather than averaging over thousands of examples, so a handful can be enough. Everything is bits and set
operations, and work happens only where something is active or changing, so it runs on ordinary CPUs, down to small
devices. Intelligence doesn't have to live in data centres; that changes what it costs the planet, and who gets to build
it.

### 6. Any scale

The same engine fits a sensor in a reed bed and the core systems of a large enterprise. Small and local is where AMP is
easiest to see. Large and high-stakes is where its traceability may be worth the most: where results must be defended
to clients, regulators and courts, and where neither rigid rules nor opaque models are good enough.

Memories compose. Volumes nest and connect. A memory can be built on another: general language first, then a domain,
then a team's own. And AMP works alongside other systems: a language model can read a memory through AMX and summarise
what it has done; an AMP memory can sit underneath an agent and keep it honest.

### 7. People stay at the helm

The world is full of heat. People have problems, they try solutions, and where problems and solutions don't fit, heat
builds. An AMP program is meant to take in the heat of a problem space, work through it, and give back one of two
things: **action it can take reliably and in good faith**, or **a clear account of what would resolve it**, so people can
turn their problem space into a solution space themselves.

AMP is a companion, not a replacement. It shows the shape of a problem; people decide. Where understanding matters, it
should show the gap rather than fill it, so the settling happens in the person, not only in the machine.

### 8. A new craft

Programming with associative memory is largely unexplored. Nobody yet knows its idioms: its equivalents of a loop, a
data structure, a design pattern. They will be discovered the way the idioms of every new medium were: by people
building, tinkering and playing, often for the pure joy of it.

---

## Why it matters

**Trust.** Systems that decide things about people, places and safety need to say why, and AMP's reasons are the
decision itself.

**Accountability at scale.** Enterprises with money and legal exposure on the line need reliability and traceability,
and today are caught between rule-based software that can't keep up and models they can't defend.

**Footprint.** Learning from little on ordinary hardware means far less energy, and far fewer gatekeepers.

**Ownership.** A memory that traces every piece of structure to its source can be owned, audited, and selectively
forgotten by the people it came from.

**Learning.** Technology that helps people understand for themselves, rather than handing them answers.

**Lowering heat.** The deepest motivation: programs that find heat, show it honestly, and help it become understanding
rather than conflict, for individuals, communities, organisations and whole systems.

---

## The craft of programming with AMP

An AMP program isn't mostly logic. Most of the work is:

1. **Designing the shape.** Which volumes exist, what feeds what, what competes with what, how sparse each must be.
   Architecture work, familiar to anyone who designs systems.
2. **Declaring what must hold.** The few rules that must never bend, as fixed structure that always wins. Also what
   *should* be there, so that its absence becomes heat.
3. **Encoding the world.** Turning readings, sounds or text into active cells, so that inputs that are alike share
   cells. Ordinary code at the edge, and as important as a good microphone.
4. **Teaching.** Curating examples.
5. **Choosing what may learn.** Some volumes fixed, some free to grow, with heavy learning scheduled for rest.
6. **Examining.** Tests are cues with expected completions, and expectations about where heat should and shouldn't
   appear. Debugging is stepping through moments and asking why one assembly won.
7. **Reviewing growth.** Reading what a memory learnt, like a pull request, and keeping or correcting it.

The language for this is meant to be **declarative inside a memory** (say what is known, then cue it with a fragment)
and **wired between volumes** (activity flowing from one to another, many parts settling at once), with a thin
scripting layer on top to run experiments and orchestrate.

---

## At every scale

Seven sketches of AMP in use, from a single device in a reed bed to an enterprise and a five-year construction
programme. Each is imagined, with the hard parts left in. Together they show the same idea at very different scales.

### 1. A sensor that learns its reed bed

A wetland reserve wants three things from a small solar-powered sensor: an alert if anyone uses a chainsaw or an
outboard motor at night, a record of when the bittern (a rare bird they're bringing back) is booming, and warning if
the soundscape starts changing in ways nobody expected.

**Design.** Sound is split into frequency bands by ordinary code and turned into active cells in a hearing volume. A
context volume holds time of day and season. A known-sounds volume holds chainsaw, engine and bittern. A volume for
normal learns what this place sounds like. Known sounds and normal compete for each moment; whatever neither explains
is heat.

**Programming.** The programmer imports a shared memory of common sounds someone else has built, then teaches local
examples: twenty recordings of this reserve's bittern, and the wardens' own boat, so it isn't mistaken for an intruder.
Chainsaw and outboard are declared fixed. The output rules: chainsaw or engine at night sends an alert; bittern is
logged; heat that stays high, with nothing explaining it, is recorded and flagged for a person.

**Testing.** Last year's recordings are replayed through AMX. Bittern clips must complete to bittern, rain and wind
must settle into normal, and deliberately odd clips must raise heat. Failures are fixed with examples, never by tuning
numbers.

**In the field.** Heat runs high for the first weeks as it learns the reed warblers, the frogs and the distant trains,
then falls. At 3am an alert arrives: outboard engine, strong match, no warden boat expected, with the clip and the
reasons. When it's wrong, a warden taps "that's our tractor," and that one example becomes structure.

**Review.** Months later, forty new assemblies have formed. One is a call that recurs at dusk every spring and isn't
explained by anything. It's a species returning to the reserve. That structure is named and shared with sensors on other
reserves.

### 2. A language that stays with its people

A small community's language has a dozen fluent speakers left, mostly elders. With the words go stories, songs, place
names and knowledge of the land.

**Faithful by design.** AMP's memory is good enough, not a perfect recording, so the original recordings are kept
alongside it. The memory holds the understanding (how words, meanings, places, stories and people connect) and every
piece links back to the exact recording that taught it. When it recalls, it doesn't paraphrase an elder. It plays the
elder.

**The community leads.** They decide what goes in and who may see what. Some knowledge is only for certain people or
seasons, and because structure traces to its source, those rules travel with it. If an elder withdraws something, it can
be found and removed. The memory lives on the community's own hardware.

**Teaching.** Elders tell stories and walk the land naming places, and each session is annealed in. Few examples are
enough, which is what this situation needs. A correction ("that word is for a river, not a stream") becomes structure at
once.

**Heat as a to-do list.** The most valuable output is what doesn't fit yet: words heard once with no context, stories
with missing pieces, places with no names. That becomes the list of questions for the next session, while the elders
are still here to answer them.

**Use.** A teenager walks the land with a phone. At a bend in the river, up come the place name, its story, and her
great-uncle's voice telling it. She tries a sentence; where the grammar doesn't fit, she hears an elder say it properly.

A language lives in people, not in a memory. AMP is scaffolding for new speakers and a record that would otherwise be
lost. The measure of success is more speakers.

### 3. A town that disagrees about a flood

A river town has flooded three times in ten years. Residents want a wall, upstream farmers fear being made the overflow,
an environmental group wants the floodplain restored, businesses fear the cost, and the council has a budget and a
deadline. The meetings have turned bitter.

**What it does and doesn't do.** The program decides nothing and says nobody is right. It shows the shape of the
disagreement, the way a good mediator would.

**Design choices that matter.** In AMP, more structure means more support, so a hundred copies of one letter could
drown out everyone else. Support is counted per person or group, not per submission, and that choice is visible to
everyone. Every affected party is declared up front, so a group that hasn't been heard shows up as heat, not silence.
Spoken testimony counts as fully as written submissions. Individuals can see and withdraw their own input; the shared
map shows views, not names. Anyone can ask why the map shows what it does and follow the trail back to the submissions.

**What the map shows.**
- **Common ground:** settled structure almost everyone shares. Nobody's home should flood, farmers shouldn't carry the
  cost alone, the river should stay healthy. There is usually more of this than the arguments suggested.
- **Heat from missing facts:** residents assume floodplain restoration means more flooding in town; farmers assume a
  wall pushes water onto their fields. Nothing in the evidence settles either. That isn't disagreement; it's an
  unanswered question. Commission the study, and much of the heat drops away.
- **Heat that won't settle:** real differences in values. The program doesn't paper over them, which would be
  patching. It names them as the decisions the town has to make together.

The council can cue options against the memory ("wall plus compensation", "partial restoration plus a lower wall") and
see which concerns each settles and which it leaves hot. The record of how the decision was reached is kept for when
the next flood comes.

### 4. A controller for a pond and three sluice gates

A farm co-operative needs to keep fields watered in dry spells, store water when it rains, and never let the pond
overtop in a storm. This is the engineer's view.

**The project** looks like any other: a Go service on a small box by the pond, with the AMP engine as a library,
ordinary code for sensors and motors, AMP files declaring the structure, folders of examples and tests, and a memory
snapshot versioned like any build artefact.

**Encoding numbers.** A pond level becomes a band of active cells in its own volume, so nearby levels share most of
their cells and empty and full share none. Choosing the bands is real engineering: too coarse and it can't tell safe from
risky; too fine and it can't generalise.

**Structure.** One volume per sensor, a context volume (season, forecast), a volume of recognised situations, and a
volume for the current step of a procedure. That last one has room for only one active cell at a time, so it acts as a
variable: "where am I in this procedure". Procedures are transitions: storm coming, open the overflow gate a step,
check, open another if still rising, hold when steady.

**Safety first.** Pond near the top means overflow fully open, declared fixed. Beyond that, if heat stays high past a
set number of moments, the service hands over to a simple conventional safe-mode controller and calls a person. When it
doesn't understand, it says so and does the simple safe thing.

**Learning from the operator.** Years of logs are replayed and annealed, so it picks up local habits, like holding water
back in late spring because the far field always dries first. The engineer reads what formed, to check it learnt the
habit and not an accident in the logs.

**The run loop.** Every minute: read sensors, encode, invoke, settle within a hard cap on moments (a controller must
answer in bounded time), read the output, move the gates, write the trace. Anneal once a day at rest, never mid-storm.

**Testing and operating.** Transcript tests (these readings, expect these actions and no heat), plus a simulated
catchment running a hundred years of synthetic weather overnight, including storms worse than any on record. Debugging
in AMT steps through the moments to see why a situation won and which example created it. Releases are snapshots that
can be compared and rolled back. Monitoring watches heat the way you'd watch error rates: a steady rise is the early
sign the world has changed, perhaps a silted channel or a new crop.

### 5. A hospital being built

A new hospital, a five-year build. Structural, mechanical, electrical, fire, medical gas and IT engineers, the client's
clinical teams, regulators and dozens of suppliers. The systems engineer's job is to hold it all together. The project
produces thousands of documents: requirements, design models, schedules, change orders, site reports, inspection
records. Misfits between them are where the money goes. A problem found in design costs a meeting; the same problem
found on site costs months.

**Design.** A volume for requirements, the client's brief and the regulations. A volume for the design, fed from the
building model: each component, which system it belongs to, where it sits. A schedule volume, where activities and
their dependencies are transitions, so it knows what must happen before what. A volume for site reality, from daily
reports, inspections and drone surveys. A volume for the commercial side: contracts and changes. To read the documents,
the program imports a general English memory, then a construction vocabulary memory, then adds the project's own
material on top.

**Setting the dial.** Regulations, fire safety, contractual obligations and hard geometry are declared fixed: they
always win and can't be learnt away. Left loose is how this particular project behaves: which supplier runs late, which
trade's reports understate problems, how changes tend to ripple.

**In use.** A mechanical change moves a duct. Geometry checkers already catch the duct hitting a beam. What they miss is
that it now passes through a fire-rated wall, and that a requirement in a different document, written three years ago,
says that wall can't be penetrated. That is a misfit of meaning across documents, and AMP raises it as heat with the
trail to both sources. A steel delivery slips, and the schedule's transitions show which later activities lose their
support, so the ripple is visible before it lands.

**Before agreeing a change.** The most valuable use: cue a proposed change against the memory. Which requirements does
it unsettle? Which activities does it push? Which contract terms does it touch? The systems engineer's hardest job,
seeing the whole consequence, becomes something they can lay out for the client as options with trade-offs.

**Trust and the law.** Construction disputes are enormous, and inquiries after failures ask one question above all:
what did they know, and when? A memory where nothing breaks can be rewound to the day a decision was made, showing what
was known, what was flagged and who saw it.

**Across projects.** Lessons-learnt documents are rarely read again. The memory from this hospital can be the starting
point for the next, so the next systems engineer begins with structure that already knows how hospitals go wrong.

**Reporting.** A language model reading through AMX writes the weekly summary for the board: what changed, what is hot,
what settled. An AMP program reading AMX's own record could go further, holding a memory of how the project's
understanding evolved and noticing when the same kind of heat keeps returning in the same part of the building.

### 6. Satellite imagery at enterprise scale

A company processes satellite imagery for large clients: crop monitoring for insurers, change detection for
governments, infrastructure checks for utilities. A lot of money rides on the results, and so do contracts and
reputations.

**The problem it faces today.** Engineers with AI assistants can write deterministic pipelines, but hand-written rules
can't keep up with the variety in the data: seasons, cloud, sensors, regions, new kinds of change. Its deep learning
models absorb the variety, but they are slow to retrain, they generalise where they shouldn't or overfit where they
mustn't, and when a client challenges a result, nobody can say exactly why the model saw what it saw.

**Setting the dial.** Each client's hard definitions are declared fixed: what counts as a field boundary, what counts as
a change worth reporting, what confidence a result must reach before it goes out. Loose is everything the data teaches:
how this region looks in each season, how this sensor drifts, how flooded fields differ from shadowed ones.

**In use.** New imagery arrives and is read against what is known. Most of it completes cleanly to familiar patterns.
Where something doesn't fit, the result goes out with its heat attached: unexplained change in this tile, these parts of
the scene unaccounted for, these rival readings tied. A new sensor or a new region doesn't mean a retraining cycle;
analysts confirm a handful of examples, and the structure grows, visibly.

**When a client challenges a result.** The company can show the evidence for that reading, the rival readings it beat,
which examples formed the structure it relied on, and the state of the memory on the day the result was issued. That
answer is the difference between keeping and losing a contract, and in some industries between passing and failing an
audit.

### 7. A memory underneath an AI agent

A coding agent is fluent but forgetful, and nobody can see what it "knows" about a codebase. AMP sits underneath it. The
memory reads the code, its history and the design decisions behind it. When the agent proposes a change, the memory
shows which parts of the system it touches, which past decisions it cuts against, and why those decisions were made,
linked to the commits and documents. When the agent claims something, the memory says whether it fits what is known or
raises heat. AMP doesn't compete with language models here. It makes them accountable.

---


---

## Learning

The realistic version of AMP's promise for learning is not that you step into a machine and come out understanding. A
map of someone else's understanding isn't yours, however readable it is, and raw cells and assemblies are as foreign to
a learner as weights are. Understandable by design becomes learnable only when views are designed for learners. Within
that, AMP offers three things.

**A map for orientation.** Much of the struggle in learning something new is not knowing its shape: what connects to
what, what is central, where an idea came from. A memory built from a field's sources gives that shape, and every piece
leads back to the original passage. It doesn't replace reading; it shows what to read next, and why.

**A mirror for your own heat.** A program can show a learner where their understanding doesn't yet fit: the claim that
clashes with what they've read, the two ideas they've never connected. Confusion becomes specific instead of a vague
sense of being lost. The design choice that matters: **show the shape of the gap, don't fill it.** If the machine
completes everything, the settling happens in the machine. If it says "these two don't fit, and here is where each came
from," the settling happens in the person.

**Building memories yourself.** People learn deepest by building things that think, as Seymour Papert argued with Logo.
Teaching a memory, watching what it gets wrong and working out why, teaches the subject and how knowing works. Unlike
teaching a person, the memory shows exactly what it took from you.

The hope behind this: that people, especially younger generations, can follow their curiosity (or their heat) wherever it
leads, and find a place where it settles, in themselves and not only in a machine. That keeps people asking what they
want, where they are going, and how to get there.

## Play

Not everyone who picks up AMP will be trying to solve the world's problems. Many will be drawn by the craft itself, and
that may matter more than any application. New crafts are made real by the people who play with them: early home
computers, the demoscene, Arduino, modular synths, people watching the Game of Life for hours to see what emerged.

AMP suits play. It is visual: cells lighting up, a whole completing from a fragment, heat draining away as something
settles. It is cheap: a laptop or a microcontroller is enough. And it is unexplored. Some starting points: a memory that
learns the birds in your garden and greets each by name; an instrument that completes your melodies in your own style;
little creatures in a simulation, each with a memory of its own; teaching a memory a game by playing it in front of it;
reading your old notebooks into a memory and wandering through how your thinking connects; or a constraint, the way the
PICO-8 community works: sixty-four cells, what is the cleverest thing you can make?

Small creations, shared and remixed, are also research: many people running quick sketches, finding the idioms the rest
of the discipline will be built on.

---

## Honesty and its limits

AMP's honesty is about its own coherence. Its limits are part of the premise, and designing for them is part of the
craft.

**Fitting is not the same as being true.** Something false that hangs together produces no heat. A well-built campaign
of misinformation is coherent; so are many conspiracy theories, often more so than the messy truth. Heat catches
contradiction, not fiction. AMP says "this doesn't fit," never "what settles is true."

**Absence is silent unless something expects it.** Heat builds around gaps that something points at. If a stakeholder's
view was never put in at all, nothing points at it, and there is no heat about its absence. The missing voice is the
most dangerous bias. The remedy is to declare what should be there: if a program holds a fixed rule that every affected
party must be represented, a missing party becomes heat.

**Volume is not weight.** In AMP, more structure means more support. A party that writes a thousand documents could
outcompete one that gives a few spoken testimonies, and knowledge that isn't written down can look like a gap when it is
only a different form. Support must be counted deliberately (per person, per party, per source) and that choice must be
visible.

**It only knows what it was given.** A confident-looking map of a biased set of sources is still biased. What AMP can do
is show its workings, so people can judge for themselves.

**Every strength cuts both ways.** A sensor that learns normal can learn the normal of people and flag whoever deviates.
A system that traces every piece of knowledge to its source can trace every opinion to the person who held it. A map of
a community's disagreements could be a manipulation guide in the wrong hands. And explanations can be over-trusted:
"it gave reasons" is not "it was right." Openness, consent and visible design choices are the basis of trust, not
optional extras.

---

## What AMP adds to existing work

AMP stands on a long line of work: Hebb's cell assemblies; Hopfield networks and the physics of settling; Kanerva's
sparse distributed memory and the hyperdimensional computing (vector symbolic architectures) that grew from it, which
also programs with sparse binary patterns on ordinary hardware; case-based reasoning; truth maintenance systems, which
detect contradictions among exact facts; and neurosymbolic AI, which seeks the same middle ground between rules and
learning from another direction.

What AMP aims to add is the combination, in one substrate: tolerant completion and competition over soft, partial
information; held context and sequence; heat as a first-class, honest output; learning that only adds, with full
history; provenance on every piece of structure; and a dial between declared and learnt structure that the engineer
controls. Whether that combination delivers more than its parts is exactly what has to be shown.

## What must be proven

The vision is ahead of the evidence. Most of it rests on things the engine cannot yet do:

- **Association between assemblies**, and transformations as reliable transitions, so that programs can chain
  retrieval, transformation and learning.
- **Scale**: settling that stays clean, and costs that follow activity, as memory grows to millions of assemblies.
  Capacity and crosstalk are real problems in every associative memory ever built.
- **The core rules at scale**: binary structure, no weights and nothing breaking are elegant, and unproven beyond small
  worlds. They may be what makes AMP work, or what it has to adapt.
- **Encoding**: how the world becomes active cells is ordinary engineering at the edge, and a poor encoding can't be
  rescued by the memory behind it.
- **Learnable views**: understandable structure becomes useful to people only through tools designed for them.

## First proofs

The vision will be judged by small, convincing demonstrations, not by its breadth. The first should test the hardest
unknown, association and transformation at a modest but real scale, rather than the easiest win. Good candidates:

- **A readable memory alongside an agent**, on a real codebase.
- **A small sensor** that learns its own normal and explains its alerts.
- **A bounded enterprise pilot**: one slice of a real pipeline, running alongside the existing system, with every
  disagreement between them explained.

Each is small enough to finish and shows something nothing else does. Together they would show the range, from one
device to an enterprise.