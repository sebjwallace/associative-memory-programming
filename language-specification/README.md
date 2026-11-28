# The AMP Language Specification

*The reference for the language people and agents write to build programs on associative memory. It records what has
been decided, explains it fully, and marks clearly what is still being worked out.*

This specification sits under two contracts. The **system contract** (`../CONTRACT.md`) says what AMP must be. The
**language contract** (`../LANGUAGE-CONTRACT.md`) says what the language must be. This specification says what the
language *is*, in detail. Where it and a contract disagree, the contract wins and this specification is corrected.

---

## Status

Every chapter and every section carries one of two markers:

- **Stable.** Decided by the owner. Implementations and examples may rely on it. It changes only by a deliberate
  decision, recorded in the chapter.
- **In progress.** Proposed or partly decided. Shown so the shape of the language is visible, but not to be relied on.
  The open question is stated next to it.

**On syntax.** The meaning of each construct is what the status refers to. The exact spelling of keywords and
punctuation is provisional throughout, even in stable sections, until the specification says otherwise. An example
may change its spelling without the construct changing its meaning.

## Chapters

| # | Chapter | Status |
|---|---|---|
| 1 | [Introduction](01-introduction.md) | Stable |
| 2 | [Notation and lexical elements](02-notation.md) | Mostly stable |
| 3 | [Types](03-types.md) | Mostly stable |
| 4 | [Values, declarations and scope](04-values-and-declarations.md) | Mostly stable |
| 5 | [Volumes, cells and cell sets](05-volumes-cells-and-cell-sets.md) | Stable, operators in progress |
| 6 | [Encoders and encodings](06-encoders-and-encodings.md) | Stable |
| 7 | [Structure: assemblies, writing and learning](07-structure.md) | Mostly stable |
| 8 | [Asking the substrate: results](08-results.md) | In progress |
| 9 | [Heat](09-heat.md) | Mostly stable |
| 10 | [Functions and effects](10-functions-and-effects.md) | Mostly stable |
| 11 | [Tests](11-tests.md) | In progress |
| 12 | [Errors](12-errors.md) | Stable |
| 13 | [Space: shaped volumes](13-space.md) | In progress |
| 14 | [Open questions](14-open-questions.md) | In progress |

## Conventions used in this specification

- **Examples use fruit** ("apple red sweet", "cherry red sour", "lemon yellow sour"), the kind of neutral example
  language specifications use, so that names in examples are never confused with words of the language.
- **Text that an encoder processes** is written in quotes: "apple".
- **Examples follow the language's own naming rule**: every name says what it holds.
- A line beginning `//` in an example is a comment. A comment showing output is written as it would be displayed.

---

## Where the language stands

The language has its **nouns** and its first **verbs**: types, values, volumes, cells, cell sets and their operators,
encoders and encodings, assemblies and writing, results and heat, functions and their effects. What it does not yet have
is its **own model of computation**: how volumes connect, and how a program runs by letting activity flow through them
and settle under heat. Until then, AMP programs read as ordinary programs that ask a memory questions. The connection of
volumes and the settling of a program are the next major topic (chapter 14), and they are what will make AMP a language
no existing one could replace.

**Space** is the next idea with a strong precedent: in the research, procedures learned and run inside associative
memory depended on content written at places and read by a moving focus. Chapter 13 sets out, as a proposal, how the
language could give space a home inside the substrate (volumes with a shape, geometry only, relations learned in
assemblies), so that a program can be seen thinking.

Learning is deliberately **not** built in. The language provides the primitives every learning method is built from, and
learning procedures are written in AMP (chapter 7), because the right way for associative memory to learn is still a
research question.

## Building the language: a suggested order

For whoever implements it. Build one step at a time, each step working and tested before the next, and keep to the
contracts: no hacks, no shortcuts, nothing hidden.

1. **Lexing and parsing** of what chapters 2 and 4 define: comments, names, literals (`Int`, `Ratio`, `Text`, `Bool`),
   `let`, `const`, `fn`, `return`, typed parameters and return types.
2. **The type checker**, with types written out everywhere and nothing inferred (chapter 3). Errors are reported before
   anything runs, in plain words (chapter 12).
3. **Ordinary evaluation**: integer and exact ratio arithmetic, comparisons, `Text`, `List`, function calls. No floating
   point.
4. **Volumes and cell sets** (chapter 5): `Volume(size:, density:)`, cells by index, `CellSet[V]`, the cell set
   operators, index checking, and the type rule that cell sets of different volumes never mix.
5. **Encoders and encodings** (chapter 6): one simple encoder (split by word, one cell per word), encodings carrying
   indexes, label and source, and cells by label.
6. **Assemblies and writing** (chapter 7): `Assembly[V]`, writing structure into a volume, `fixed`, sources recorded on
   every assembly, and the rule that only marked volumes can be written to (chapter 10).
7. **Asking**: `complete` and `touch`, returning results with heat (chapters 8 and 9). The result and heat designs are
   still in progress here: build the smallest version that keeps heat honest, and expect it to change.
8. **Tests** (chapter 11), so every later step can be checked in AMP itself.

Everything marked **in progress** should be built only as far as the steps above need, and always in the form the
specification proposes, so that the owner can see it working and then decide.
