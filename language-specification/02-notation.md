# 2 · Notation and lexical elements

**Status: Mostly stable.** The rules for names, casing and literals are stable. The exact spelling of punctuation is
provisional.

## 2.1 Comments

**Stable in meaning, provisional in spelling.** A comment runs from `//` to the end of the line.

```
// A volume for fruit names.
let fruit: Volume = Volume(size: 64, density: 2% to 10%)   // 64 cells
```

## 2.2 Names

**Stable.** A name says what it holds. Single letters and abbreviations are not used: `apple_cue`, not `a`;
`fruit_lines`, not `fl`. This is an idiom of the language, and tooling may warn on names that break it. It applies to
examples above all, because examples become the idiom.

**Casing. Stable.**

- **Types** are written in PascalCase: `Volume`, `CellSet`, `HeatModel`.
- **Values, variables, functions and parameters** are written in lowercase with underscores: `fruit`, `apple_cue`,
  `sized_volume`.
- A volume's name is a value, so it stays lowercase even inside a type: `CellSet[fruit]` reads "a CellSet of fruit".

## 2.3 Keywords

**In progress.** The words reserved so far are:

| Keyword | Meaning | Status |
|---|---|---|
| `let` | names a value | Stable |
| `const` | names a value known before the program runs | Stable |
| `fn` | defines a function | Stable in meaning |
| `return` | returns a value from a function | Stable in meaning |
| `fixed` | marks structure that can never be outcompeted | Stable |
| `write` | puts structure into a volume | Stable in meaning; the verb is not yet confirmed |
| `using` | names the encoder whose labels a statement uses | In progress |
| `mut` | marks a parameter whose volume a function changes | In progress |
| `defer` | runs a statement when the enclosing scope ends | In progress |
| `match` | acts on the shape of a result | In progress |
| `test`, `expect` | define and check tests | In progress |
| `requires`, `ensures` | contracts on a function | In progress |
| `true`, `false` | the two Bool values | Stable |
| `to` | the range between two values, as in a density range | Stable in meaning |
| `in` | whether one cell set lies within another | In progress |

## 2.4 Literals

**Stable.**

- **Integers:** `0`, `64`, `200`. Type `Int`.
- **Ratios:** written as a percentage (`2%`), or constructed from two integers (`Ratio(1, 50)`). `2%` is exactly the
  ratio 1/50. Type `Ratio`. There are no floating-point literals (chapter 3).
- **Text:** in double quotes: `"apple red sweet"`. Type `Text`.
- **Booleans:** `true`, `false`. Type `Bool`.

## 2.5 Brackets

**Stable in meaning.** Each kind of bracket has one job:

| Bracket | Job | Example |
|---|---|---|
| `( )` | calling and constructing | `Volume(size: 64, ...)` |
| `{ }` after a volume | a set of cells in that volume | `fruit{3, 7}` |
| `{ }` after an encoder | the encoding for a label | `words{"red"}` |
| `{ }` as a block | the body of a function or test | `fn ... { ... }` |
| `[ ]` after a type | the type's parameter | `CellSet[fruit]`, `List[Encoding]` |
| `[ ]` after a list | an item by position, counted from 1 | `apple_line[1]` |
| `< >` | an assembly | `<"apple", "red", "sweet">` |

Angle brackets belong to assemblies alone; types use square brackets so the two never clash.

## 2.6 Operators

**Stable in principle; symbols in progress.** Arithmetic uses the usual operators on `Int` and `Ratio`: `+`, `-`, `*`, `/`,
and comparisons `==`, `!=`, `<`, `<=`, `>`, `>=`. Cell sets have their own operators (chapter 5): `+` union, `&`
intersection, `-` difference, `^` symmetric difference, `==` equality and `in` containment. An operator's meaning follows
the types it is used on, and mixing types is an error.

Angle brackets mean an assembly when they enclose its members, as in `<"apple", "red">`, and a comparison only between
numbers. Keeping comparisons to numbers keeps the two readings from ever meeting.

