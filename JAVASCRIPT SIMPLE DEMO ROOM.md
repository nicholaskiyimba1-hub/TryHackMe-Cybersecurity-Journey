# JavaScript: Simple Demo Room

## Introduction

This room introduced the basics of **JavaScript** by building a simple **"Guess the Number"** game.

The game works by having the computer randomly select a number between **1 and 20**, after which the user repeatedly guesses the number. The program provides feedback indicating whether the guess is too high, too low, or correct.

The room focused on three fundamental programming concepts:

- Variables
- Conditional statements
- Loops/iterations

The program was executed using **Node.js**, allowing JavaScript code to run from the terminal.

---

## 1. Running JavaScript with Node.js

JavaScript was originally designed primarily for execution inside web browsers. However, **Node.js** provides a runtime environment that allows JavaScript to run outside the browser.

In this room, JavaScript programs were executed from the terminal using:

```bash
node filename.js
```

For example:

```bash
node guess_v3.js
```

The room used Node.js throughout the exercises rather than executing the JavaScript through a browser.

---

## 2. Variables

A variable is a named location used to store a value that can change during program execution.

JavaScript uses the `let` keyword to declare variables.

For the guessing game, two important variables were:

```javascript
let tries = 0;
let guess = 0;
```

### `tries`

`tries` keeps track of how many attempts the user has made.

It starts at:

```javascript
let tries = 0;
```

Each time the user makes a guess, it is increased by one:

```javascript
tries = tries + 1;
```

### `guess`

`guess` stores the number entered by the user.

It initially starts at `0`:

```javascript
let guess = 0;
```

This is outside the valid range of 1–20, ensuring it cannot accidentally match the secret number before the user makes a guess.

---

## 3. Constants

JavaScript also provides the `const` keyword for values that should not be reassigned.

The game's secret number is stored in a constant:

```javascript
const secret = Math.floor(Math.random() * 20) + 1;
```

The `secret` should remain unchanged throughout the game, so `const` is appropriate.

### Generating the Random Number

The expression:

```javascript
Math.floor(Math.random() * 20) + 1
```

generates a random integer from **1 to 20**.

The process is:

1. `Math.random()` generates a decimal from `0` up to, but not including, `1`.
2. Multiplying by `20` produces a value from `0` up to almost `20`.
3. `Math.floor()` removes the decimal portion.
4. Adding `1` shifts the range to `1–20`.

For example:

```text
Math.random() → 0.372
× 20          → 7.44
Math.floor()  → 7
+ 1           → 8
```

The resulting secret number is therefore within the required range.

---

## 4. Displaying Output

JavaScript uses:

```javascript
console.log()
```

to display information in the terminal.

For example:

```javascript
console.log("I'm thinking of a number between 1 and 20");
```

This displays:

```text
I'm thinking of a number between 1 and 20
```

---

## 5. Getting User Input

The game needs to receive guesses from the user.

Because the program is being executed through Node.js, the room uses the `readline` module to interact with the terminal.

The required modules are imported with:

```javascript
import * as readline from "node:readline/promises";
import { stdin as input, stdout as output } from "node:process";
```

A readline interface is then created:

```javascript
const rl = readline.createInterface({ input, output });
```

The program can now ask the user for input:

```javascript
const text = await rl.question("Take a guess: ");
```

The user's response is initially received as text.

It is converted into an integer using:

```javascript
guess = parseInt(text, 10);
```

Therefore:

```text
User input → text → parseInt() → integer → guess
```

---

## 6. Cleaning Up the Readline Interface

After creating the readline interface, it should be closed when the program finishes.

The room uses:

```javascript
rl.close();
```

The interface is placed inside a `try...finally` structure:

```javascript
try {
    // Program code
} finally {
    rl.close();
}
```

The `finally` block ensures that the readline interface is closed when execution leaves the `try` block.

---

# 7. Conditional Statements

The next step was making the game respond to the user's guess.

The program needs to determine whether the guess is:

1. Outside the valid range
2. Too low
3. Too high
4. Correct

JavaScript uses `if`, `else if`, and `else` for this.

```javascript
if (guess < 1 || guess > 20) {
    console.log("That number is out of range. Try again.");
} else if (guess < secret) {
    console.log("Too low, try again.");
} else if (guess > secret) {
    console.log("Too high, try again.");
} else {
    console.log("You got it in", tries, "tries!");
}
```

### Understanding the Conditions

The first condition checks whether the number is outside the valid range:

```javascript
guess < 1 || guess > 20
```

The `||` operator means **OR**.

The second condition checks whether the guess is smaller than the secret:

```javascript
guess < secret
```

If true, the program reports:

```text
Too low, try again.
```

The third condition checks whether the guess is greater than the secret:

```javascript
guess > secret
```

If true:

```text
Too high, try again.
```

Finally, if none of the previous conditions are true, the guess must equal the secret:

```javascript
else {
    console.log("You got it in", tries, "tries!");
}
```

---

## 8. Example of Conditional Logic

Suppose:

```text
secret = 10
```

If the user guesses:

```text
15
```

the condition:

```javascript
guess > secret
```

is true.

The program displays:

```text
Too high, try again.
```

If the user guesses:

```text
35
```

the first condition is true because `35 > 20`.

The program displays:

```text
That number is out of range. Try again.
```

---

# 9. Iterations and While Loops

At this stage, the program only allowed the user to make one guess.

To turn it into an actual game, the program needs to continue asking for guesses until the correct number is found.

A `while` loop is used:

```javascript
while (guess !== secret) {
    // Instructions repeated here
}
```

The condition:

```javascript
guess !== secret
```

means:

> Continue looping while the guess is not equal to the secret number.

The JavaScript operator:

```javascript
!==
```

means **not equal**.

---

## 10. The `tries` Variable

Every time the user makes another guess, the number of attempts increases:

```javascript
tries = tries + 1;
```

Therefore, `tries` records how many guesses the user has made.

For example:

```text
Guess 1 → tries = 1
Guess 2 → tries = 2
Guess 3 → tries = 3
Guess 4 → tries = 4
```

When the correct guess is finally made, the program reports the total number of attempts.

---

# 11. Final Program

The final version of the game combines:

- Variables
- Constants
- Random number generation
- User input
- Type conversion
- Conditional statements
- A `while` loop
- Output
- Cleanup

The main structure is:

```javascript
import * as readline from "node:readline/promises";
import { stdin as input, stdout as output } from "node:process";

const rl = readline.createInterface({ input, output });

try {
    const secret =
        Math.floor(Math.random() * 20) + 1;

    let tries = 0;
    let guess = 0;

    console.log("I'm thinking of a number between 1 and 20");

    while (guess !== secret) {
        const text = await rl.question("Take a guess: ");

        guess = parseInt(text, 10);

        tries = tries + 1;

        if (guess < 1 || guess > 20) {
            console.log("That number is out of range. Try again.");
        } else if (guess < secret) {
            console.log("Too low, try again.");
        } else if (guess > secret) {
            console.log("Too high, try again.");
        } else {
            console.log("You got it in", tries, "tries!");
        }
    }
} finally {
    rl.close();
}
```

---

# 12. Running the Game

The final program was available as:

```text
/home/ubuntu/JavaScript-Demo/guess_v3.js
```

It can be executed with:

```bash
cd /home/ubuntu/JavaScript-Demo
node guess_v3.js
```

An example execution is:

```text
I'm thinking of a number between 1 and 20
Take a guess: 10
Too low, try again.
Take a guess: 15
Too high, try again.
Take a guess: 13
Too low, try again.
Take a guess: 14
You got it in 4 tries!
```

Each time the program is started again, a new secret number is generated.

---

# 13. Key JavaScript Concepts Learned

| Concept | JavaScript |
|---|---|
| Declare a variable | `let` |
| Declare a constant | `const` |
| Display output | `console.log()` |
| Generate random value | `Math.random()` |
| Round down | `Math.floor()` |
| Convert text to integer | `parseInt()` |
| Conditional statement | `if / else if / else` |
| OR operator | `||` |
| While loop | `while` |
| Not equal | `!==` |
| Increase a value | `tries = tries + 1` |
| Close readline | `rl.close()` |

---

# 14. Key Takeaways

This room provided my first practical introduction to JavaScript.

The most important concepts I learned were the three basic building blocks of imperative programming:

### Variables

Variables store values that can change during program execution.

```javascript
let tries = 0;
let guess = 0;
```

### Conditionals

Conditionals allow a program to make decisions based on conditions.

```javascript
if (guess < secret) {
    console.log("Too low, try again.");
}
```

### Loops

Loops allow instructions to be repeated.

```javascript
while (guess !== secret) {
    // Repeat the game logic
}
```

I also learned how Node.js can execute JavaScript from the command line and how the `readline` module can be used to receive user input.

---

# Conclusion

The **JavaScript: Simple Demo** room introduced the fundamentals of JavaScript through a practical guessing game rather than simply presenting isolated syntax.

The program was gradually developed from a simple script that generated a random number and accepted one guess into a complete interactive game that repeatedly accepts guesses and provides feedback.

The most important concepts from the room were:

- `let` and `const`
- `Math.random()` and `Math.floor()`
- `console.log()`
- `readline`
- `parseInt()`
- `if / else if / else`
- `while` loops
- Comparison and logical operators
- Tracking program state with variables

The room also provided a useful comparison with the **Python: Simple Demo** room, showing that the same programming logic can be implemented using different programming languages and syntax.