# TryHackMe — Pre Security: Data Representation

## Overview

The **Data Representation** room introduced me to the fundamental ways computers represent information internally.

Humans normally work with the decimal (base-10) number system, but computers operate using binary states represented as `0` and `1`. The room connected this concept to computer graphics, showing how colors can be represented using binary and hexadecimal values.

This room covered:

* Binary numbers
* Decimal numbers
* Hexadecimal numbers
* Octal numbers
* Bits and bytes
* RGB color representation
* Hexadecimal color codes
* Converting between different number systems

These concepts are particularly important in cybersecurity because binary and hexadecimal representations appear frequently when working with networking, memory, file formats, packet analysis, cryptography, and security tools.

---

## Task 1 — Introduction

Computers ultimately work with two states, which can be represented as:

```text
0 = Off / Low
1 = On / High
```

A single binary digit is called a **bit**.

Humans commonly use the decimal system, which contains ten digits:

```text
0 1 2 3 4 5 6 7 8 9
```

Computers use the binary system, which contains only:

```text
0 1
```

The purpose of this room was to understand how combinations of these binary states can represent much more complex information, including numbers and colors.

### Learning Objectives

The room focused on:

* Representing 8 colors
* Representing more than 16 million colors
* Understanding binary numbers
* Understanding hexadecimal numbers
* Understanding octal numbers

**Question:** No answer needed.

---

# Task 2 — Representing Colors

## RGB Color Representation

Computers can represent colors using the **RGB color model**:

* **R** — Red
* **G** — Green
* **B** — Blue

Each component controls the intensity of one primary color.

To understand this, imagine that each color channel can only have two states:

```text
0 = Off
1 = On
```

There are therefore three bits:

```text
RGB
```

Each bit has two possible states, giving:

```text
2 × 2 × 2 = 8
```

Therefore, three bits can represent **8 different RGB combinations**.

### The 8 Basic Colors

| Binary | RGB State    | Color   |
| ------ | ------------ | ------- |
| `000`  | All off      | Black   |
| `001`  | Blue on      | Blue    |
| `010`  | Green on     | Green   |
| `011`  | Green + Blue | Cyan    |
| `100`  | Red on       | Red     |
| `101`  | Red + Blue   | Magenta |
| `110`  | Red + Green  | Yellow  |
| `111`  | All on       | White   |

This was my first practical demonstration of how combinations of bits can represent something more meaningful than just numbers.

---

## From 8 Colors to 16.7 Million Colors

Modern RGB color representation provides much more than two intensity levels.

Each RGB channel can use **8 bits**.

Since 8 bits can represent:

```text
2⁸ = 256
```

different values, each channel can have 256 possible intensity levels.

There are three channels:

```text
256 × 256 × 256
```

which gives:

```text
16,777,216
```

possible RGB combinations.

Therefore, a standard 24-bit RGB color can represent **16.7 million colors**.

### Why 24 bits?

Each color channel uses one byte:

```text
Red   = 8 bits
Green = 8 bits
Blue  = 8 bits
```

Therefore:

```text
8 + 8 + 8 = 24 bits
```

or:

```text
3 bytes
```

---

## Bits and Bytes

A **bit** is a binary digit and can contain either:

```text
0
```

or:

```text
1
```

A **byte** consists of 8 bits.

Therefore:

```text
1 byte = 8 bits
```

An 8-bit value can represent:

```text
2⁸ = 256
```

different values, ranging from:

```text
0–255
```

This is why an RGB color channel can have 256 intensity levels.

---

## Hexadecimal Color Representation

Representing a 24-bit color entirely in binary would be difficult to read.

For example:

```text
10100011 11101010 00101010
```

Hexadecimal makes this much easier.

One hexadecimal digit represents exactly **4 bits**.

For example:

```text
A = 1010
3 = 0011
E = 1110
```

The hexadecimal system contains 16 symbols:

```text
0 1 2 3 4 5 6 7 8 9 A B C D E F
```

The letters represent values 10–15:

| Decimal | Hexadecimal | Binary |
| ------: | :---------: | :----: |
|       0 |     `0`     | `0000` |
|       1 |     `1`     | `0001` |
|       2 |     `2`     | `0010` |
|       3 |     `3`     | `0011` |
|       4 |     `4`     | `0100` |
|       5 |     `5`     | `0101` |
|       6 |     `6`     | `0110` |
|       7 |     `7`     | `0111` |
|       8 |     `8`     | `1000` |
|       9 |     `9`     | `1001` |
|      10 |     `A`     | `1010` |
|      11 |     `B`     | `1011` |
|      12 |     `C`     | `1100` |
|      13 |     `D`     | `1101` |
|      14 |     `E`     | `1110` |
|      15 |     `F`     | `1111` |

Since every hexadecimal digit represents 4 bits, two hexadecimal digits represent 8 bits — exactly one byte.

Therefore, a 24-bit RGB color can be represented using six hexadecimal digits:

```text
RRGGBB
```

For example:

```text
#A3EA2A
```

The first two digits represent red, the next two green, and the final two blue.

---

## Room Questions

### 1. Color `#3BC81E`

Using the room's color preview, `#3BC81E` appears **green**.

### 2. Binary representation of `#EB0037`

Convert each hexadecimal digit into its 4-bit binary equivalent:

```text
E = 1110
B = 1011
0 = 0000
0 = 0000
3 = 0011
7 = 0111
```

Therefore:

```text
#EB0037
= 1110 1011 0000 0000 0011 0111
```

### 3. Decimal representation of `#D4D8DF`

Each pair represents one RGB channel:

```text
D4 = 212
D8 = 216
DF = 223
```

Therefore:

```text
RGB = (212, 216, 223)
```

---

# Task 3 — Numbers: Decimal to Hexadecimal

## Decimal — Base 10

The decimal system is the number system humans commonly use.

It contains ten digits:

```text
0–9
```

The value of each digit depends on its position.

For example:

```text
213
```

can be written as:

```text
2 × 10² + 1 × 10¹ + 3 × 10⁰
```

which gives:

```text
2 × 100 + 1 × 10 + 3 × 1
= 200 + 10 + 3
= 213
```

This positional concept also applies to binary and hexadecimal, but the base changes.

---

## Binary — Base 2

Binary has only two possible digits:

```text
0
1
```

Each position represents a power of 2.

For example:

```text
1001
```

can be expanded as:

```text
1 × 2³
+ 0 × 2²
+ 0 × 2¹
+ 1 × 2⁰
```

Therefore:

```text
8 + 0 + 0 + 1 = 9
```

So:

```text
1001₂ = 9₁₀
```

### Binary Place Values

For a 4-bit number:

| Bit position | 2³ | 2² | 2¹ | 2⁰ |
| ------------ | -: | -: | -: | -: |
| Value        |  8 |  4 |  2 |  1 |

This gives us an easy way to convert binary to decimal.

For example:

```text
1101
```

means:

```text
8 + 4 + 0 + 1 = 13
```

Therefore:

```text
1101₂ = 13₁₀
```

---

# Hexadecimal — Base 16

Hexadecimal is a base-16 number system.

It uses:

```text
0–9
A–F
```

The letters represent:

```text
A = 10
B = 11
C = 12
D = 13
E = 14
F = 15
```

The important relationship between binary and hexadecimal is:

```text
1 hexadecimal digit = 4 bits
```

For example:

```text
F = 1111
A = 1010
B = 1011
```

This makes hexadecimal extremely useful for representing binary data in a shorter and more readable form.

---

## Converting Hexadecimal to Decimal

Hexadecimal uses powers of 16.

For example:

```text
9BDF
```

can be expanded as:

```text
9 × 16³
+ B × 16²
+ D × 16¹
+ F × 16⁰
```

Replacing the hexadecimal letters with their decimal values:

```text
9 × 4096
+ 11 × 256
+ 13 × 16
+ 15 × 1
```

which gives:

```text
36864 + 2816 + 208 + 15
= 39903
```

Therefore:

```text
0x9BDF = 39903
```

---

# Octal — Base 8

The octal system uses eight digits:

```text
0–7
```

It is a base-8 number system.

The relationship between binary and octal is:

```text
1 octal digit = 3 bits
```

For example:

```text
7 = 111
6 = 110
5 = 101
```

An example conversion is:

```text
357₈
```

Expanding it:

```text
3 × 8²
+ 5 × 8¹
+ 7 × 8⁰
```

Therefore:

```text
3 × 64 + 5 × 8 + 7
= 192 + 40 + 7
= 239
```

So:

```text
357₈ = 239₁₀
```

Octal is less commonly encountered than hexadecimal in modern cybersecurity work, but understanding it helps reinforce how positional number systems work.

---

## Task 3 Questions

### 1. Convert hexadecimal `FF` to binary

Each `F` represents:

```text
F = 1111
```

Therefore:

```text
FF = 1111 1111
```

Answer:

```text
11111111
```

### 2. Convert hexadecimal `AB` to decimal

```text
A = 10
B = 11
```

Therefore:

```text
AB = 10 × 16¹ + 11 × 16⁰
```

```text
= 160 + 11
= 171
```

Answer:

```text
171
```

### 3. Convert `FF FF FF` to decimal

Each `FF` represents 255.

Therefore:

```text
FF FF FF
= 255 × 256² + 255 × 256 + 255
```

This gives:

```text
16,777,215
```

Rounded to the nearest million:

```text
17 million
```

Answer:

```text
17 million
```

---

# Task 4 — Conclusion

This room introduced the fundamental number systems used by computers and showed how binary data can represent much more than simple numbers.

The main concepts I learned were:

### Decimal

**Base 10**

```text
0–9
```

This is the number system humans commonly use.

### Binary

**Base 2**

```text
0–1
```

Computers use binary representations to encode information from underlying two-state physical systems.

### Hexadecimal

**Base 16**

```text
0–9, A–F
```

Each hexadecimal digit represents 4 binary bits, making hexadecimal a compact and readable representation of binary data.

### Octal

**Base 8**

```text
0–7
```

Each octal digit represents 3 binary bits.

---

## Color Representation

I also learned how computers represent colors using the RGB model.

A standard 24-bit RGB color consists of:

```text
8 bits → Red
8 bits → Green
8 bits → Blue
```

Therefore:

```text
24 bits = 3 bytes
```

Each channel can represent 256 intensity levels:

```text
2⁸ = 256
```

Combining the three channels gives:

```text
256 × 256 × 256
= 16,777,216
```

possible colors.

This is why a six-digit hexadecimal color such as:

```text
#3BC81E
```

can represent an RGB color.

---

## Key Takeaways

The most important things I took from this room are:

1. A **bit** can represent either `0` or `1`.
2. **8 bits = 1 byte**.
3. Binary is **base 2**.
4. Decimal is **base 10**.
5. Hexadecimal is **base 16**.
6. Octal is **base 8**.
7. One hexadecimal digit represents **4 bits**.
8. One octal digit represents **3 bits**.
9. A standard RGB color uses **24 bits / 3 bytes**.
10. RGB can represent **16,777,216 possible colors**.
11. Hexadecimal is particularly useful because it provides a compact representation of binary data.

---

## Cybersecurity Relevance

Understanding binary and hexadecimal is not just a mathematical exercise.

These representations appear throughout cybersecurity and IT, including:

* Network packet analysis
* IP and MAC addresses
* File headers and magic bytes
* Memory analysis
* Cryptographic values
* Hashes
* Permissions and bitwise operations
* Reverse engineering
* Digital forensics
* Exploit development
* Low-level programming

This room therefore provided some of the fundamental knowledge needed for the more technical cybersecurity topics that follow in the **TryHackMe Pre Security** pathway.

## Next Room

The next room is **Data Encoding**, where the focus moves from representing numbers and colors to representing text, characters, and other forms of data.

---

**Platform:** TryHackMe
**Path:** Pre Security
**Room:** Data Representation
**Focus:** Binary, hexadecimal, octal, bits, bytes, and RGB color representation
