# TryHackMe — Pre Security: Data Encoding

## Overview

The **Data Encoding** room builds on the previous **Data Representation** room.

In the previous room, I learned that computers represent data using bits and numbers. This room extended that idea to **text, symbols, and emojis**.

The key concept is that characters are represented by numbers according to an agreed standard called an **encoding**.

For example, a computer does not inherently understand the letter `A` as a letter. Instead, an encoding system assigns `A` a numerical value. The computer stores and processes that numerical representation.

This room covered:

- ASCII
- ASCII limitations
- Extended character encodings
- Unicode
- Unicode code points
- UTF-8
- UTF-16
- UTF-32
- Emoji representation
- Character encoding problems and gibberish

---

# Task 1 — Introduction

## Representation vs Encoding

One of the most important concepts from this room was the distinction between **representation** and **encoding**.

### Representation

Representation describes how information exists internally as bits and numbers.

For example:

```text
01000001
```

is simply a sequence of bits.

### Encoding

Encoding gives those numbers a specific meaning.

Under ASCII:

```text
01000001 = A
```

Therefore, the same underlying concept of storing information as numbers can be used to represent letters, punctuation, digits, and other characters.

A text string is therefore essentially a sequence of numerical character codes stored as binary data.

---

## Why Encoding Matters

If a file is saved using one encoding and later interpreted using another incompatible encoding, the characters may appear incorrectly.

This can result in what looks like:

```text
Ã©
â€™
� 
```

or other forms of unintelligible text.

This happens because the program reading the data is interpreting the stored bytes according to a different character encoding than the one used when the data was originally encoded.

---

## Learning Objectives

The room introduced:

- ASCII
- Unicode
- UTF-8
- UTF-16
- UTF-32
- Emoji encoding
- Character encoding problems

**Question:** No answer needed.

---

# Task 2 — ASCII

## What is ASCII?

**ASCII** stands for:

> American Standard Code for Information Interchange

ASCII is an early character encoding standard introduced in 1963.

The original ASCII standard uses **7 bits**, allowing it to represent:

```text
2⁷ = 128
```

different values.

Therefore, ASCII defines codes from:

```text
0–127
```

These codes represent English letters, numbers, punctuation, and control characters.

---

## ASCII Examples

Some important ASCII values are:

| Decimal | Hexadecimal | Binary | Character |
|---:|:---:|:---:|:---:|
| 48 | `30` | `00110000` | `0` |
| 49 | `31` | `00110001` | `1` |
| 57 | `39` | `00111001` | `9` |
| 65 | `41` | `01000001` | `A` |
| 66 | `42` | `01000010` | `B` |
| 90 | `5A` | `01011010` | `Z` |
| 97 | `61` | `01100001` | `a` |
| 98 | `62` | `01100010` | `b` |
| 122 | `7A` | `01111010` | `z` |
| 127 | `7F` | `01111111` | DEL |

One useful pattern is that characters are arranged sequentially.

For example:

```text
a = 97
b = 98
c = 99
```

and:

```text
A = 65
B = 66
C = 67
```

This makes it possible to determine nearby character codes without memorizing the entire ASCII table.

---

# Representing "TryHackMe" in ASCII

Suppose I save the following text:

```text
TryHackMe
```

Using ASCII, every character is converted into a numerical code.

At the binary level, it becomes:

```text
01010100 01110010 01111001 01001000 01100001
01100011 01101011 01001101 01100101
```

These binary values correspond to:

```text
T r y H a c k M e
```

If the file also contains a newline after the text, another character is stored to represent the newline.

---

## The Same Data in Hexadecimal

Binary is useful for understanding what is happening at the bit level, but it is difficult for humans to read.

The same ASCII data can therefore be represented in hexadecimal:

```text
54 72 79 48 61 63 6B 4D 65
```

For example:

```text
54 = T
72 = r
79 = y
48 = H
61 = a
63 = c
6B = k
4D = M
65 = e
```

This demonstrates an important relationship:

```text
Character
   ↓
ASCII code
   ↓
Binary / hexadecimal representation
```

---

# Limitations of ASCII

ASCII was designed primarily around the English language.

This created problems when computers needed to represent characters from other languages.

For example:

```text
ñ
é
ü
ł
č
ř
```

are not part of the original 7-bit ASCII character set.

An additional eighth bit allowed systems to represent another 128 values, but different regions created different character encodings.

Examples include:

- ISO-8859-1 (Latin-1)
- ISO-8859-2 (Latin-2)
- Windows-1252

The problem was that these encodings did not necessarily assign the same values to the same characters.

For example, data encoded using one regional encoding could be interpreted incorrectly using another.

This created compatibility problems and could result in characters being displayed incorrectly.

---

# Task 2 Questions

## 1. ASCII code for `@`

The decimal ASCII code for:

```text
@
```

is:

```text
64
```

## 2. Character with ASCII code `35`

ASCII decimal:

```text
35
```

represents:

```text
#
```

## 3. Character with ASCII code `7`

ASCII decimal:

```text
7
```

represents the **BEL** control character.

Unlike normal printable characters, this is a control character rather than something normally displayed as a visible symbol.

---

# Task 3 — Unicode

## Why Unicode Was Needed

ASCII works well for basic English text, but the world's writing systems contain far more characters than ASCII can represent.

Examples include:

```text
ñ
Ω
あ
ب
龍
😊
♞
```

Using different regional encodings to solve this problem created compatibility issues.

The same byte could potentially be interpreted as different characters depending on which encoding was being used.

A universal system was therefore needed.

---

# Unicode

**Unicode** is a universal character standard designed to assign unique identifiers to characters across writing systems.

These identifiers are called **code points**.

Unicode code points are normally written using:

```text
U+
```

followed by hexadecimal digits.

Examples:

| Character | Unicode Code Point |
|---|---|
| `A` | `U+0041` |
| `Ω` | `U+03A9` |
| `あ` | `U+3042` |
| `ت` | `U+062A` |
| `♞` | `U+265E` |

The important idea is that Unicode gives characters a universal identity.

---

# Unicode vs UTF

A distinction I learned from this room is that **Unicode and UTF are not exactly the same thing**.

Unicode defines the characters and their code points.

UTF encoding formats define how those Unicode code points are represented as bytes.

The three encoding forms covered in this room were:

- UTF-8
- UTF-16
- UTF-32

---

# UTF-8

UTF-8 is one of the most widely used Unicode encoding formats, particularly on the modern web.

It uses between:

```text
1–4 bytes
```

depending on the character.

ASCII characters retain their original one-byte representation.

For example:

```text
A = U+0041
```

and UTF-8 represents it using one byte.

More complex characters require additional bytes.

For example:

```text
Ω
```

requires two bytes in UTF-8, while many emoji require four bytes.

### Why UTF-8 is useful

UTF-8 provides:

- Compatibility with ASCII
- Support for Unicode
- Variable-length encoding
- Efficient storage for common ASCII text

---

# UTF-16

UTF-16 generally represents Unicode characters using either:

```text
2 bytes
```

or:

```text
4 bytes
```

Characters that fit within the basic range can use one 16-bit unit.

Characters outside that range, including many emoji, can require two 16-bit units.

For example:

```text
A = U+0041
```

while an emoji such as:

```text
🔥
```

requires a pair of UTF-16 code units.

---

# UTF-32

UTF-32 takes a simpler approach.

Every Unicode code point occupies exactly:

```text
4 bytes
```

For example:

```text
A
```

can be represented as:

```text
U+00000041
```

and:

```text
🔥
```

as:

```text
U+0001F525
```

The advantage is simplicity: every code point occupies the same amount of space.

The disadvantage is that it uses considerably more storage than UTF-8 for many types of text.

---

# Emoji and Unicode

An important realization from this room was that emojis are not fundamentally different from other characters from the computer's perspective.

For example:

```text
😊
```

has the Unicode code point:

```text
U+1F60A
```

Similarly:

```text
🔥
```

has:

```text
U+1F525
```

The computer does not store a literal picture of the emoji. It stores encoded numerical data that software interprets and renders using a suitable font or graphical representation.

---

# Other Unicode Examples

The room provided several useful examples:

| Character | Unicode |
|---|---|
| `龍` | `U+9F8D` |
| `😊` | `U+1F60A` |
| `ツ` | `U+30C4` |
| `シ` | `U+30B7` |
| `ت` | `U+062A` |
| `♞` | `U+265E` |

This shows how one universal standard can represent characters from completely different writing systems.

---

# Task 3 Questions

## 1. UTF-32 encoding of `😌`

The Unicode code point for:

```text
😌
```

is:

```text
U+1F60C
```

Therefore, its UTF-32 representation is:

```text
U+0001F60C
```

---

## 2. UTF-16 encoding of `シ`

The character:

```text
シ
```

has Unicode code point:

```text
U+30B7
```

Its UTF-16 representation is:

```text
U+30B7
```

This is different from:

```text
ツ = U+30C4
```

which is important because the two Japanese characters look somewhat similar but are different Unicode characters.

---

## 3. Character represented by `U+2615`

The Unicode code point:

```text
U+2615
```

represents:

```text
☕
```

the hot beverage symbol.

---

## 4. Character represented by `U+2658`

The Unicode code point:

```text
U+2658
```

represents:

```text
♘
```

the white chess knight.

---

# Task 4 — Conclusion

This room showed me how computers can represent human-readable text using numerical data.

The progression can be summarized as:

```text
Bits
 ↓
Numbers
 ↓
Character codes
 ↓
Text
```

ASCII was one of the earliest widely used standards for representing characters, but its 7-bit design was primarily suited to English.

Regional encodings attempted to extend character support, but using different standards created compatibility problems.

Unicode addressed this by providing a universal system of code points for characters across different writing systems.

UTF-8, UTF-16, and UTF-32 then provide different ways of encoding those Unicode code points into computer-readable byte sequences.

---

# Key Takeaways

### ASCII

- Uses 7 bits.
- Defines 128 character codes.
- Primarily designed around English.
- Includes letters, numbers, punctuation, and control characters.

### Unicode

- Provides a universal character standard.
- Assigns unique code points to characters.
- Supports many writing systems, symbols, and emoji.

### UTF-8

- Uses 1–4 bytes per encoded character.
- ASCII-compatible.
- Very common on the modern web.

### UTF-16

- Uses 2 or 4 bytes for Unicode characters.
- Some characters require surrogate pairs.

### UTF-32

- Uses exactly 4 bytes per Unicode code point.
- Simple but less space-efficient.

---

# Cybersecurity Relevance

Understanding character encoding is important in cybersecurity because security tools frequently process data at the byte and character level.

Encoding knowledge is useful when dealing with:

- Web requests
- HTTP headers and parameters
- Log analysis
- Network traffic
- File analysis
- Digital forensics
- Malware analysis
- Command-line data
- Character encoding attacks
- Web application security
- Data sanitization and validation

Encoding problems can also become security problems. If two systems interpret the same bytes differently, an application may validate one representation while another component interprets it differently.

Therefore, understanding the relationship between **bytes, encodings, and characters** is an important foundation for later cybersecurity work.

---

## What I Learned

The most important lesson from this room was that **text is ultimately stored as numerical data**.

A character that looks simple to a human, such as:

```text
A
```

is represented internally using an agreed numerical encoding.

For example:

```text
A
↓
U+0041
↓
UTF-8 / UTF-16 / UTF-32 representation
↓
Binary data
```

This helped connect the previous **Data Representation** room to the way real computers store and transmit text.

---

**Platform:** TryHackMe  
**Path:** Pre Security  
**Room:** Data Encoding  
**Focus:** ASCII, Unicode, UTF-8, UTF-16, UTF-32, and character representation
