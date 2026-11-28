# 1 · Introduction

**Status: Stable.**

## 1.1 What AMP is

AMP (Associative Memory Programming) is a language for building software around associative memory. A program
declares **volumes** of **cells**, turns outside input into activity in them, puts **structure** (assemblies) into
them by hand or by learning, and **asks** them questions. Every answer from a volume says not only what it found but
how well it fitted, what was left unexplained (**heat**), which rivals it could not choose between (**ties**), and
where everything came from (**sources**).

## 1.2 The substrate

Everything a running AMP program holds (every cell in every volume, all the structure between them, and the activity
and heat within them) is the **substrate**. The word comes from materials: one interconnected material in which
structure forms, like atoms joined by bonds, and in which heat lives. The substrate may be held in RAM while a program
runs, or stored on disk; it is the same substrate either way.

A **volume** is a bounded part of the substrate with behaviour of its own. Programs work with volumes; the substrate
is what they are all part of.

## 1.3 What the language is like

AMP is shaped by its contracts. In practice that means:

- **Clear and explicit.** Every value's type is written out. Every change to the substrate is visible in the code.
  Nothing happens that the code does not show.
- **Recognisable.** Its everyday syntax follows modern languages (types after names, braces, `fn`, `//` comments), so a
  programmer who knows Rust, TypeScript, Swift or Kotlin can follow it on first sight. Its philosophy draws on older,
  principled languages: Prolog and Datalog (say what you want), Ada and SPARK (explicit declarations, contracts),
  Lustre (moments and flow), Lisp (a small core).
- **Honest.** Uncertainty is never dropped. A result that carries heat passes it on; a tie is held, not guessed.
- **Deterministic.** The same program, input and substrate version always give the same results.
- **Small.** A few constructs, each earning its place, with everything else written in AMP itself.

## 1.4 How programs run

AMP programs run through an **interpreter**, which defines what the language means and makes stepping through,
inspecting and asking "why" natural. Speed comes from the **associative memory engine** underneath, which is native
and optimised, not from compiling scripts. Compiling may come later (chapter 14); if it does, compiled programs must
give exactly the same results as the interpreter.
