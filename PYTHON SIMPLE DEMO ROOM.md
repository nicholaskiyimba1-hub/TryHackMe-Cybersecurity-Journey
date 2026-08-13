# Python: Simple Demo

## Overview

This room was my introduction to **Python programming**.

The previous rooms in the Pre Security pathway focused on how computers represent and encode information. This room moved from understanding computer data to actually writing instructions that a computer can execute.

The practical project was a simple **Guess the Number** game.

The computer randomly selects a number between `1` and `20`, and the user repeatedly guesses until the correct number is found.

The room introduced three fundamental programming concepts:

- Variables
- Conditional statements
- Loops / iteration

---

# Task 1 — Introduction

## What is Python?

Python is a **high-level, general-purpose programming language**.

High-level means that Python hides many of the low-level implementation details involved in communicating directly with the computer.

General-purpose means Python can be used for many different tasks, including:

- Automation
- Web development
- Data analysis
- Machine learning
- Scripting
- System administration
- Cybersecurity

For this room, Python was used to create a simple interactive program.

---

## The Guess the Number Game

The game follows three basic steps:

1. The computer secretly chooses a number between `1` and `20`.
2. The user enters guesses.
3. The computer tells the user whether the guess is too high, too low, or correct.

A successful execution might look like:

```text
I'm thinking of a number between 1 and 20
Take a guess: 10
Too high, try again.
Take a guess: 5
Too low, try again.
Take a guess: 7
Too low, try again.
Take a guess: 8
You got it in 4 tries!
```

Although the program is simple, it demonstrates concepts that are fundamental to programming.

---

## Learning Objectives

The main objectives of this room were to learn:

- Python variables
- Conditional statements
- Iteration using loops

---

# Task 2 — Variables

Before writing the complete game, I first had to understand how the program stores information.

The game needs to keep track of three important pieces of information:

```text
secret
guess
tries
```

### `secret`

This stores the random number selected by the computer.

### `guess`

This stores the user's current guess.

### `tries`

This keeps track of how many guesses the user has made.

---

## Generating the Secret Number

Python provides the `random` module for generating random values.

The program begins with:

```python
import random

secret = random.randint(1, 20)
tries = 0
guess = 0

print("I'm thinking of a number between 1 and 20")
```

### Breaking it down

```python
import random
```

This imports Python's `random` module so that the program can generate random numbers.

```python
secret = random.randint(1, 20)
```

This generates a random integer between `1` and `20` and stores it in the `secret` variable.

```python
tries = 0
```

At the beginning of the game, the user has not made any guesses, so the number of attempts starts at zero.

```python
guess = 0
```

The initial guess is set to `0`.

This is outside the valid range of `1–20`, so it cannot accidentally equal the secret number before the user makes a guess.

```python
print("I'm thinking of a number between 1 and 20")
```

This displays information to the user.

---

## Getting User Input

The program then needs to allow the user to enter a guess.

```python
text = input("Take a guess: ")
guess = int(text)

tries = tries + 1
```

There are several important concepts here.

### `input()`

The `input()` function waits for the user to enter something.

The value returned by `input()` is a **string**.

For example, if the user enters:

```text
15
```

Python initially receives it as text.

### `int()`

The program needs to perform mathematical comparisons with the guess.

Therefore, the text is converted into an integer:

```python
guess = int(text)
```

The program can now compare the guess numerically with the secret number.

### Counting Attempts

Every time the user makes a guess:

```python
tries = tries + 1
```

increases the number of attempts by one.

---

## Incomplete Version

At this stage, the program can:

1. Generate a secret number.
2. Ask the user for a guess.
3. Convert the input into an integer.
4. Count the attempt.

However, it cannot yet tell the user whether the guess is correct.

That requires **conditional statements**, which are introduced in the next task.

---

## Task 2 Questions

### Question 1

**What is the name of the function used to display text on the screen?**

Answer:

```text
print()
```

### Question 2

**What is the name of the function used to convert user input to an integer?**

Answer:

```text
int()
```

---

# Task 3 — Conditional Statements

The program now needs to make decisions based on the user's guess.

For example:

- Is the number outside the allowed range?
- Is it too low?
- Is it too high?
- Is it correct?

This is where **conditional statements** are useful.

---

## `if`, `elif`, and `else`

Python uses:

```python
if
elif
else
```

to execute different sections of code depending on whether conditions are true or false.

The game's decision-making logic is:

```python
if guess < 1 or guess > 20:
    print("That number is out of range. Try again.")
elif guess < secret:
    print("Too low, try again.")
elif guess > secret:
    print("Too high, try again.")
else:
    print("You got it in", tries, "tries!")
```

---

## Understanding the Logic

### First condition

```python
if guess < 1 or guess > 20:
```

This checks whether the user's guess is outside the allowed range.

For example:

```text
50
```

is greater than `20`, so the condition is true.

The program responds:

```text
That number is out of range. Try again.
```

---

### Second condition

```python
elif guess < secret:
```

If the first condition was false, Python checks whether the guess is smaller than the secret number.

For example, if:

```text
secret = 10
guess = 5
```

then:

```text
5 < 10
```

is true.

The program therefore displays:

```text
Too low, try again.
```

---

### Third condition

```python
elif guess > secret:
```

If the previous conditions were false, Python checks whether the guess is greater than the secret number.

For example:

```text
secret = 10
guess = 15
```

Since:

```text
15 > 10
```

the program displays:

```text
Too high, try again.
```

---

### Final `else`

If none of the previous conditions are true, the guess must equal the secret number.

Therefore:

```python
else:
    print("You got it in", tries, "tries!")
```

indicates a successful guess.

---

## The First Working Version

The resulting program was:

```python
import random

secret = random.randint(1, 20)
tries = 0
guess = 0

print("I'm thinking of a number between 1 and 20")

text = input("Take a guess: ")
guess = int(text)

tries = tries + 1

if guess < 1 or guess > 20:
    print("That number is out of range. Try again.")
elif guess < secret:
    print("Too low, try again.")
elif guess > secret:
    print("Too high, try again.")
else:
    print("You got it in", tries, "tries!")
```

The limitation was that the user only received **one opportunity** to guess.

The next step was therefore to make the program repeat until the correct number was found.

---

## Task 3 Questions

### Question 1

**How does Python write "else if"?**

Answer:

```python
elif
```

### Question 2

**What will the program display if the user's input is `50`?**

Answer:

```text
That number is out of range. Try again.
```

---

# Task 4 — Iterations

The game is much more useful if the user gets multiple attempts.

This introduces the concept of **iteration**, commonly implemented using loops.

A loop allows a program to repeatedly execute the same block of code while a particular condition remains true.

---

## The `while` Loop

Python provides the `while` loop for this type of situation.

The important condition is:

```python
guess != secret
```

The operator:

```text
!=
```

means **not equal to**.

Therefore:

```python
while guess != secret:
```

means:

> Continue executing the loop while the user's guess is not equal to the secret number.

---

## How the Loop Works

The program starts with:

```python
guess = 0
```

and the secret number is somewhere between `1` and `20`.

Since the initial guess cannot equal the secret:

```text
guess != secret
```

is true.

The program enters the loop and asks for a guess.

Suppose:

```text
secret = 10
guess = 5
```

The condition becomes:

```text
5 != 10
```

which is true.

The loop therefore runs again.

If the user eventually enters:

```text
10
```

the condition becomes:

```text
10 != 10
```

which is false.

The loop terminates.

---

## Completed Program

The final version of the game is:

```python
import random

secret = random.randint(1, 20)

tries = 0
guess = 0

print("I'm thinking of a number between 1 and 20")

while guess != secret:
    text = input("Take a guess: ")
    guess = int(text)

    tries = tries + 1

    if guess < 1 or guess > 20:
        print("That number is out of range. Try again.")
    elif guess < secret:
        print("Too low, try again.")
    elif guess > secret:
        print("Too high, try again.")
    else:
        print("You got it in", tries, "tries!")
```

This version combines the three major concepts introduced throughout the room:

```text
Variables
    ↓
Conditionals
    ↓
Loop
```

---

## Understanding the Complete Program

The program first creates the variables:

```python
secret = random.randint(1, 20)
tries = 0
guess = 0
```

It then informs the user that a number has been selected:

```python
print("I'm thinking of a number between 1 and 20")
```

The `while` loop keeps the game running:

```python
while guess != secret:
```

Inside the loop, the program:

1. Gets user input.
2. Converts the input to an integer.
3. Increases the attempt counter.
4. Compares the guess with the secret.
5. Gives the appropriate feedback.

The process continues until:

```text
guess == secret
```

---

## Task 4 Questions

### Question 1

**What type of loop does this program use?**

Answer:

```text
while loop
```

### Question 2

**What will the program display if the user makes the correct guess in 3 tries?**

Answer:

```text
You got it in 3 tries!
```

---

# Task 5 — Conclusion

This room introduced three fundamental pillars of imperative programming:

## 1. Variables

Variables allow programs to store information.

Examples from the game include:

```python
secret
guess
tries
```

---

## 2. Conditionals

Conditional statements allow programs to make decisions.

The game uses:

```python
if
elif
else
```

to determine whether a user's guess is:

- Out of range
- Too low
- Too high
- Correct

---

## 3. Loops

Loops allow code to execute repeatedly.

The game uses:

```python
while guess != secret:
```

to continue asking for guesses until the user finds the correct number.

---

# Key Takeaways

The most important concepts I learned from this room were:

- Python is a high-level, general-purpose programming language.
- Variables store values that a program can use.
- `input()` receives input from the user.
- `int()` converts a value to an integer.
- `print()` displays information.
- `if`, `elif`, and `else` allow a program to make decisions.
- `while` allows a section of code to repeat while a condition remains true.
- `!=` means "not equal to".
- Programs can combine variables, conditions, and loops to create interactive applications.

---

# Cybersecurity Relevance

Python is particularly important in cybersecurity because it can be used to automate repetitive tasks and build security tools.

The concepts learned here form the foundation for more advanced Python scripting.

For example, later cybersecurity scripts may use:

```text
Variables
    ↓
Conditions
    ↓
Loops
    ↓
Functions
    ↓
File handling
    ↓
Networking
    ↓
Automation
```

Understanding these basic programming concepts is therefore important before moving into more advanced security automation and scripting.

---

# Final Result

By the end of the room, I had worked through the development of a simple Python game:

```text
Random number generation
        ↓
User input
        ↓
Variable storage
        ↓
Conditional comparisons
        ↓
Repeated guesses using a while loop
        ↓
Successful result
```

The final task confirmed that I had successfully run my first Python game.

**Room completed:** Python: Simple Demo

**Main skills practiced:**

- Python variables
- User input
- Integer conversion
- Conditional logic
- `if / elif / else`
- `while` loops
- Random number generation
- Basic Python scripting