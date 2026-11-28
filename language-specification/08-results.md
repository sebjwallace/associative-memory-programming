# 8 · Asking the substrate: results

**Status: In progress.** The rule for when a result is returned, and the name `Result`, are stable. The fields of a
result and the shapes it can take are proposals.

## 8.1 When a result is returned

**Stable.** What an operation returns depends on what it did:

| Operation | Returns |
|---|---|
| Asking a volume (`complete`, `touch`, and others to come) | a `Result[V]` |
| Writing structure | an `Assembly[V]` |
| Reading a volume's activity or heat | a `CellSet[V]` or a `Heat[V]` |
| Cell set operators | a `CellSet[V]` |
| Construction and arithmetic | plain values |

Only operations that ask the substrate can be uncertain (find one answer, several equally good answers, part of one,
or nothing), so only they return a result. Everything else returns plain values. The type always shows which.

## 8.2 The primitives that ask

**In progress.**

- **`complete`**: given a cue, return the whole that the cue completes to. Rivals compete; the better supported wins;
  a true tie is held.
- **`touch`**: given a cue, return every assembly the cue reaches, ranked by how much of each it covers. Nothing
  competes, so touch produces no ties.

Others (stepping along transitions, letting activity settle) are expected and not yet specified.

## 8.3 What a result holds

**In progress.** The proposal:

- **candidates:** each a cell set, the assembly it completed to, and how well it fitted (the name "candidate" is a
  placeholder);
- **heat:** a `Heat[V]` (chapter 9);
- **ties:** candidates that were equally supported and held open;
- **cue:** what was asked;
- **sources:** where everything involved came from;
- **version:** which version of the substrate answered.

```
let words: Encoder = Encoder(split: "word", cells: 1)
let fruit: Volume = Volume(size: 64, density: 2% to 10%)

let apple: Assembly[fruit] = write fruit using words <"apple", "red", "sweet"> fixed
let cherry: Assembly[fruit] = write fruit using words <"cherry", "red", "sour">

let apple_completion: Result[fruit] = complete(fruit, fruit{words{"apple"}})
//    candidates   apple           1 of 3 given, 2 recalled
//    heat         none
//    ties         none

let red_completion: Result[fruit] = complete(fruit, fruit{words{"red"}})
//    candidates   apple, cherry   1 of 3 each
//    ties         apple | cherry
//    heat         contested: "red"

let banana_completion: Result[fruit] = complete(fruit, fruit{words{"banana"}})
//    candidates   none
//    heat         unexplained: "banana"

let red_touch: Result[fruit] = touch(fruit, fruit{words{"red"}})
//    candidates   apple, cherry   each touched 1 of 3
//    ties         none
```

### Results at more than one level

**In progress.** When structure includes abstractions and compositions, one cue can settle at a general level while
staying open at a specific one. With `red_things` (what apple and cherry share) in the volume:

```
let red_completion: Result[fruit] = complete(fruit, fruit{words{"red"}})
//    settled      red_things             3 of 3
//    tied         apple | cherry          1 of 3 each
//    reached      fruit_pair              through both
```

In plain words: "it is one of the red things, but I can't tell which." A flat list of candidates cannot say that, so the
result design is expected to report what settled at the general level and what is still open at the specific level.
How a program then picks the best-supported candidate (written `reading.best` in chapter 7) depends on this design.

## 8.4 Results cannot be ignored

**Stable.** A result must be used: stored, returned, passed on or examined. Discarding one silently is an error. When a
function builds its answer from several results, their heat and ties carry through into what it returns.

## 8.5 Acting on the shape of a result

**In progress.** The proposal is a `match` that must handle every shape a result can take, so a tie can never be
forgotten:

```
match red_completion {
   settled(answer)       => ...,
   tied(first, second)   => ...,
   incomplete(answer)    => ...,
   nothing               => ...,
}
```
