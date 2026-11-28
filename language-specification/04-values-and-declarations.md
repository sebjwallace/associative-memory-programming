# 4 · Values, declarations and scope

**Status: Mostly stable.** Immutability, `let` and `const` are stable. Temporary volumes and `defer` are in progress.

## 4.1 Values are immutable

**Stable.** Once made, a value never changes. Cell sets, encodings, assemblies, results and heat stay as they were
created. Operations produce new values rather than altering old ones.

```
let apple: CellSet[fruit] = fruit{apple_line}
let apple_and_lemon: CellSet[fruit] = apple + lemon   // apple is unchanged
```

The substrate itself does change, but only through writing (chapter 7), and the substrate's history is
never lost (the system contract: nothing breaks).

## 4.2 `let`

**Stable.** `let` gives a name to a value for the rest of its scope. Because values are immutable and names cannot be
reassigned, a `let` always means the same value wherever it is used.

```
let fruit_text: Text = "apple red sweet"
```

## 4.3 `const`

**Stable.** `const` names a value that is known **before the program runs**, in the sense of Rust, C++ and Zig. The
interpreter can check constants, and the engine can plan around them: a volume whose size comes from constants has a
size known in advance.

```
const cells_per_word: Int = 4
const fruit_count: Int = 200
let fruit: Volume = Volume(size: fruit_count * cells_per_word, density: 1% to 3%)
```

Hand-tuned numbers (for example, in sizes and densities) should be named constants, never bare numbers buried in an
expression, so every tuning choice is visible.

## 4.4 Scope

**Stable.** A name is visible from where it is declared to the end of the block that contains it. Names declared at
the top of a file are visible throughout the file.

**No hidden global volumes. Stable.** A function works only on the volumes it is given as parameters or creates
itself. It cannot reach for a volume it was not given.

## 4.5 Temporary volumes and `defer`

**In progress.** A volume created inside a function lives until it is dropped. The proposal follows Zig: clean-up is
written explicitly, next to the creation, with `defer`, so nothing is dropped out of sight.

```
fn compare_fruit(words: Encoder, first_text: Text, second_text: Text) -> Bool {
   let scratch: Volume = Volume(size: 32, density: Ratio(1, 10) to Ratio(1, 4))
   defer scratch.drop()
   ...
}
```

**Open:** whether clean-up is explicit (`defer`, as here) or automatic at the end of the scope; and how the type
system stops a function from returning a cell set, assembly or result of a volume it has dropped.
