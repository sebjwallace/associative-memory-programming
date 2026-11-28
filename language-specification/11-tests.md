# 11 · Tests

**Status: In progress.** That tests are part of the language is stable. Their syntax, and the built-in tests for
learning, are proposals.

## 11.1 Tests are part of the language

**Stable.** Tests are written in AMP, next to the code they check, and run with one command. A test gives an input and
states what must hold, including where heat and ties must or must not appear.

## 11.2 What tests are for in AMP

**Stable.** Structure comes from sources, and tests check behaviour. When new structure outcompetes old, a test breaks,
and that is where the engineer looks. Because the substrate is deterministic, a test always gives the same outcome for
the same substrate version.

## 11.3 Writing a test

**In progress.**

```
test "apple and cherry share red" {
   let shared: CellSet[fruit] = apple & cherry
   expect shared == fruit{words{"red"}}
}

test "a known fruit is cool" {
   let apple_completion: Result[fruit] = complete(fruit, fruit{words{"apple"}})
   expect apple_completion.heat.total == 0
}
```

## 11.4 Tests for learning procedures

**In progress.** Some hard-wiring can only be caught by running a procedure (chapter 7). The proposal is that the test
framework provides three tests for any learning procedure:

- **Relabelling.** Rename every label consistently ("apple" becomes "zork", "red" becomes "blee", and so on) and learn
  again. A procedure that genuinely learns does not care what things are called, so it must form the same shape of
  structure. A procedure that depends on particular words fails.
- **Held-out input.** Structure learnt from some input must handle input it never saw. If it only works on what it was
  given, it memorised rather than learnt.
- **Empty input.** Run the procedure with no input. Any structure that still forms came from the program, not the world.

## 11.5 Interpreter and compiler

If AMP is ever compiled, every test runs on both, and both must agree.
