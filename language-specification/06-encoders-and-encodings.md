# 6 · Encoders and encodings

**Status: Stable**, except where marked.

## 6.1 Encoders

**Stable.** An encoder is the boundary between the outside world and the substrate. It turns input (text today;
readings, sound or images later) into encodings. An encoder is ordinary, deterministic code at the edge of a program,
declared so that its choices are visible.

```
let words: Encoder = Encoder(split: "word", cells: 1)     // one encoding per word, one cell per word
```

Encoders and volumes are **independent of each other**. An encoder knows nothing about volumes, and a volume knows
nothing about encoders. An encoder returns encodings that can be used for many things, one of which is a volume.

*Why:* each part stays simple and general, and the boundary with the world can be changed without touching the substrate.

An encoder states how wide its output is (the highest index it uses), so a volume too small for it is caught before
anything runs.

**In progress:** the full set of encoder options, and the built-in encoders AMP provides.

## 6.2 Encodings

**Stable.** An encoding is what an encoder returns for one step of input. It carries three things:

- **indexes:** which positions are active, as bare numbers that belong to no volume yet;
- **a label:** what they stand for, such as "apple";
- **a source:** where it came from (the input, file and position).

A whole input is a list of encodings, one per step:

```
let apple_line: List[Encoding] = words.encode("apple red sweet")

// apple_line[1]   "apple"   {3}    source: fruit.amp, line 4, word 1
// apple_line[2]   "red"     {7}    source: fruit.amp, line 4, word 2
// apple_line[3]   "sweet"   {9}    source: fruit.amp, line 4, word 3
```

**Sources begin here.** The system contract requires every piece of structure to keep its source. Only the encoder
knows where input came from, so the encoder is where provenance starts, and everything downstream carries it on.

## 6.3 From encodings to cell sets

**Stable.** A volume turns an encoding into one of its own cell sets:

```
let apple_word: CellSet[fruit] = fruit{apple_line[1]}      // one step
let apple: CellSet[fruit] = fruit{apple_line}              // a whole list: all its steps at once
```

Asking an encoder for a label gives an encoding, not a cell set, because an encoding belongs to no volume:

```
let red_encoding: Encoding = words{"red"}
let red: CellSet[fruit] = fruit{red_encoding}
```

The same encoding can be used with any number of volumes, or none.

**Note.** A list of encodings turned into one cell set means "all at once". When a list is fed to a volume over time,
it means "one step after another". The two meanings must stay distinct.
