# 12 · Errors

**Status: Stable.**

## 12.1 Errors and heat are different

An **error** is a failure: the program cannot do what it says. **Heat** is uncertainty in a valid answer. A tie is not
an error; an empty cell set is not an error; a cue that explains nothing returns a result with heat, not an error.

## 12.2 Kinds of error

- **Type errors**, caught before running: a value of the wrong type, or of the wrong volume.
- **Index errors**: an index outside a volume.
- **Effect errors**: changing a volume that a function was not allowed to change.
- **Ignored results**: a result discarded without being used.
- **Contract errors**: a function's `requires` or `ensures` not met (in progress, chapter 10).
- **Limit reached**: a repetition that hit its declared limit is reported; whether it is an error or part of the result
  is in progress.
- **Outside failures**: a missing file, unreadable input.

```
fruit{70}
// error: index 70 is outside fruit (1..64)

apple & other{3}
// error: can't intersect a CellSet of fruit with a CellSet of other
```

## 12.3 Errors explain themselves

Every error names what failed, where, and why, in plain words. Like the rest of AMP, an error is meant to be read and
understood, not decoded.
