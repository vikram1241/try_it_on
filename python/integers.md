# python_integers.md

## Definition of Integer
An integer in Python is a whole number that can be positive, negative, or zero, without any decimal points or fractions. For example, 5, -3, 0, or 100 are integers. In programming terms, it's a built-in data type called `int` (short for integer), which Python uses to store and work with these numbers.

If you're completely new to programming, think of an integer like counting apples: you can't have half an apple in a count (that's a whole number). Python lets you use integers for anything from simple math to complex calculations, and it's one of the simplest data types to start with.

## What and Why Integers
**What**: Integers represent exact, whole numbers. They are used in everyday programming tasks like counting items (e.g., number of users in your app), indexing positions (e.g., the 1st item in a list), or performing calculations where precision matters (no rounding errors).

**Why**: In programming, you need a way to handle numbers without decimals to avoid mistakes. For instance, if you're building a shopping cart in your e-commerce app, the quantity of shirts must be a whole number (you can't buy 1.5 shirts). Integers are efficient for memory and fast for operations like addition or looping. Without them, tasks like repeating an action 10 times (using a loop) or calculating totals would be inaccurate or complicated.

Integers are essential because they form the basis for more advanced concepts, like controlling program flow (e.g., "if score > 10") or data structures (e.g., array sizes).

## Detailed Explanation How Integers Work in Python
Let's break this down step by step for beginners:

1. **Creation and Storage**: When you assign a number like `x = 5`, Python creates an integer object in memory. Unlike some languages (e.g., Java, where integers are "primitive" types—meaning basic, non-object data with fixed size), in Python, everything is an object. So integers are non-primitive; they are instances of the `int` class, which means they have methods (functions attached to them) and can be of unlimited size. This is called "arbitrary precision"—Python automatically handles very large numbers without overflow (e.g., 10**1000 is fine, while in Java, it would exceed limits).

2. **Immutability**: Integers are immutable, meaning once created, you can't change their value. If you do `x = x + 1`, Python creates a new integer object for the result and points `x` to it. This makes them safe to share across your code without unexpected changes.

3. **Operations**: Python supports basic math:
   - Addition (+), subtraction (-), multiplication (*), exponent (**), modulo (%) for remainder.
   - Division: / gives float (e.g., 5/2 = 2.5), // gives integer floor division (5//2 = 2).
   Python handles negative numbers seamlessly (e.g., -5 + 3 = -2).

4. **Number Systems**: Integers can be in decimal (base 10, default), binary (0b prefix, e.g., 0b101 = 5), octal (0o prefix, e.g., 0o10 = 8), or hexadecimal (0x prefix, e.g., 0xA = 10). This is useful for low-level programming like bit operations.

5. **Type Conversion**: You can convert other types to int: `int(3.9)` → 3 (truncates, doesn't round), `int("42")` → 42, `int("101", 2)` → 5 (binary to decimal). If invalid (e.g., int("abc")), it raises ValueError—always handle with try/except for safe code.

6. **Memory and Performance**: Small integers (-5 to 256) are cached (interned) for speed—same object reused. Large ones are created fresh. Operations are fast, but for huge numbers, they slow down slightly due to arbitrary precision.

7. **Primitive vs Non-Primitive**: In languages like Java or C#, "primitive" types are basic building blocks (not objects, fixed size, stored on stack). In Python, there are no true primitives—integers are objects (non-primitive), inheriting from `object` class, with methods like bit_length(). This makes Python easier but slightly slower for massive computations.

If you're starting from zero, practice by opening Python interactive shell (type `python` in terminal) and experiment: `>>> 2 + 3` → 5.

## Syntax
- Basic assignment: `age = 25` (positive), `debt = -100` (negative), `zero = 0`
- With bases: `binary = 0b1101` (13 in decimal), `octal = 0o77` (63), `hex = 0xFF` (255)
- Long integers: `big = 12345678901234567890` (no limit)
- Conversion: `num = int(input("Enter number: "))` (from string), `whole = int(4.7)` → 4
- In expressions: `result = (5 + 3) * 2 ** 3 % 7` → 1 (order: **, *, %, +)

Remember, no commas in large numbers: use underscores for readability, e.g., `million = 1_000_000`.

## Sample Code Example
Let's build a simple program step by step:

```python
# Step 1: Define integers
length = 10  # positive
width = 5
height = -2  # negative (though unusual for dimensions, for demo)
zero = 0

# Step 2: Operations
area = length * width  # 50
volume = area * abs(height)  # Use abs() to make positive: 100
power = 2 ** 3  # 8
mod = 10 % 3  # 1 (remainder)
div = 10 // 3  # 3 (floor, ignores remainder)

# Step 3: Print results
print("Area:", area)  # Area: 50
print("Volume:", volume)  # Volume: 100
print(f"Power: {power}, Mod: {mod}, Div: {div}")  # Power: 8, Mod: 1, Div: 3

# Step 4: Conversion and input
user_input = input("Enter a number: ")  # e.g., "42"
num = int(user_input)  # Convert to int
print("You entered:", num + 1)  # Adds 1

# Step 5: Large number example
huge = 10 ** 100  # 1 followed by 100 zeros
print("Huge number length:", len(str(huge)))  # 101 (includes the 1)
```

Run this in a file (save as integers.py, run `python integers.py`). If error, check input is numeric.

## Methods
Integers have built-in methods (call like num.method()). Here's each with one-line definition and example:

- `bit_length()`: Number of bits to represent in binary (excluding sign/zeros). Example: `(42).bit_length()` → 6 (101010)
- `to_bytes(length, byteorder, signed=False)`: Convert to bytes array. Example: `(255).to_bytes(2, 'big')` → b'\x00\xff'
- `from_bytes(bytes, byteorder, signed=False)`: Create int from bytes (class method). Example: `int.from_bytes(b'\x00\xff', 'big')` → 255
- `conjugate()`: Returns self (for complex compatibility; integers have no imaginary part). Example: `(7).conjugate()` → 7
- `real`: Returns the real part (always self for int). Example: `( -4).real` → -4
- `imag`: Returns imaginary part (always 0 for int). Example: `(9).imag` → 0
- `__abs__()`: Absolute value (via abs() function). Example: `abs(-10)` → 10
- `__floor__()`: Floor value (self, via math.floor). Example: `import math; math.floor(8)` → 8
- `__ceil__()`: Ceiling value (self, via math.ceil). Example: `math.ceil(8)` → 8
- `__round__(ndigits=0)`: Round to ndigits (for int, returns self). Example: `round(8, 2)` → 8

## 10 Interview Questions
1. What makes Python integers different from those in languages like C or Java?
2. Explain arbitrary precision and give an example where it's useful.
3. What is the difference between / and // for integer division?
4. How do you represent and convert binary/octal/hex integers?
5. What happens if you try int("abc") and how to handle it?
6. Why are integers immutable, and what does that mean for performance?
7. Describe integer caching in Python and its range.
8. How does bit_length() work, and when is it useful?
9. Explain negative integers in binary representation in Python.
10. Is int primitive or non-primitive in Python, and why does it matter?

## 10 Coding Interview Questions
1. Write code to reverse an integer (e.g., 123 → 321, -123 → -321, handle overflow if any).
2. Check if an integer is palindrome without converting to string.
3. Find the sum of all digits in an integer.
4. Implement a function to check if a number is prime.
5. Calculate factorial of n iteratively and recursively.
6. Find GCD of two integers using Euclidean algorithm.
7. Convert integer to binary string manually (no bin()).
8. Count set bits (1s) in binary representation.
9. Implement pow(x, n) efficiently (binary exponentiation).
10. Find the single number in an array where others appear twice (XOR).

## Links for YouTube Reference Videos
1. "Python Integers Explained" by Corey Schafer (https://www.youtube.com/watch?v=khKv-8q7YmY) - 10min beginner tutorial on basics and operations.
2. "Understanding Python Data Types: Integers" by freeCodeCamp (part of full course: https://www.youtube.com/watch?v=khKv-8q7YmY&t=120s) - Simple explanations with examples.
3. "Python Tutorial for Beginners - Integers" by Programming with Mosh (https://www.youtube.com/watch?v=_uQrJ0TkZlc&t=300s) - Covers syntax, math, and common mistakes.
4. "Arbitrary Precision Integers in Python" by Socratica (https://www.youtube.com/watch?v=PyWK9r7gHUI) - 5min on large numbers.
5. "Python Integers Methods and Operations" by Telusko (https://www.youtube.com/watch?v=9f4rvaYcJHI) - Hands-on with methods like bit_length.

Watch these in order—start with basics, then advanced. Pause and type along!