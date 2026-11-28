# 10 · Functions and effects

**Status: Mostly stable.** Typed signatures and the rule that changes to the substrate are visible are stable. The
`mut` marker and function contracts are in progress.

## 10.1 Functions

**Stable.** A function has a name, typed parameters and a typed return value. Functions work only on the volumes they
are given or create themselves.

```
fn find_fruit(fruit: Volume, words: Encoder, cue_text: Text) -> Result[fruit] {
   let fruit_cue: CellSet[fruit] = fruit{words.encode(cue_text)}
   let fruit_completion: Result[fruit] = complete(fruit, fruit_cue)
   return fruit_completion
}
```

Functions are named as actions: `find_fruit`, `sized_volume`, `learn_by_overlap`.

## 10.2 Reading and changing

**Stable in principle.** A function either only reads the substrate, or changes it, and the signature shows which.
Functions that only read can be called anywhere, in any order, any number of times, and leave the substrate exactly as
it was. Only writing changes the substrate's structure (chapter 7); learning procedures are functions that write.

**In progress: the marker.** The proposal follows Rust's mutable references: the parameter whose volume a function
changes is marked `mut`. That is more precise than marking the whole function: a function working with two volumes
says exactly which one it changes, and no word for the whole substrate is needed.

```
fn learn_by_overlap(fruit: mut Volume, words: Encoder, line_text: Text) -> List[Assembly[fruit]] {
   ...
   let abstraction: Assembly[fruit] = write fruit <shared>
   ...
}

fn find_fruit(fruit: Volume, words: Encoder, cue_text: Text) -> Result[fruit] {
   ...   // only reads: writing into fruit here would be an error
}
```

Writing into a volume that was not marked `mut`, or calling a function that does, would be an error.

## 10.3 Contracts on functions

**In progress.** Following SPARK, Dafny and Verus, a function may state conditions checked every time it runs:
`requires` before it starts, `ensures` on what it returns. A broken contract is an error.

```
fn colour_of(fruit: Volume, words: Encoder, fruit_name: Text) -> Result[fruit]
   ensures result.ties == none
{
   ...
}
```

## 10.4 Loops and limits

**Stable.** Every repetition that might not stop by itself declares an upper limit, and reaching the limit is
reported. The limit is a safeguard, not a way of steering the answer.

## 10.5 Determinism

**Stable.** The same program, given the same input and the same version of the substrate, always gives the same
results, including the same heat and ties. Nothing is decided by chance.
