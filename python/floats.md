### python_floats.md

## Definition of Float
A float in Python is a number with a decimal point or in scientific notation, representing real numbers with fractional parts. It is a built-in data type denoted as `float`.

## What and Why Floats
**What**: Floats handle non-whole numbers, like 3.14 or 2.5e3 (2500.0). They are used for measurements (e.g., height 1.75m), calculations with precision (e.g., prices $9.99), or scientific data (e.g., temperature 37.5°C).

**Why**: Integers can't represent fractions, so floats are essential for real-world apps like your virtual try-on (e.g., precise inseam 32.5 inches) or e-commerce (e.g., discounted price 49.99). They allow division to give exact results (5/2 = 2.5). However, floats have precision limits (about 15 decimal digits) due to binary representation, leading to rounding errors (e.g., 0.1 + 0.2 = 0.30000000000000004)—use decimal module for money.

Floats are key for math libraries (e.g., numpy in AI for your Gen AI textures).

## Detailed Explanation How Floats Work in Python
For absolute beginners: A program is like a recipe—floats are ingredients for "partial" amounts (half a cup = 0.5). In Python:

1. **Creation and Storage**: `x = 3.14` creates a float object. Python uses IEEE 754 double-precision (64 bits: 1 sign bit, 11 exponent, 52 mantissa), allowing ~15 decimal digits accuracy. Scientific notation: `2.5e3` = 2500.0 (e for exponent).

2. **Immutability**: Like integers, floats are immutable—operations create new objects.

3. **Operations**: Same as integers (+ - * / ** %), but / always gives float. Mixing int/float promotes to float (5 + 2.0 = 7.0). Be careful with precision: use `round(0.1 + 0.2, 1)` → 0.3 to fix errors.

4. **Type Conversion**: `float(5)` → 5.0, `float("3.14")` → 3.14, `int(3.9)` → 3 (truncate). Invalid: float("abc") raises ValueError.

5. **Primitive vs Non-Primitive**: Floats are non-primitive objects in Python (instances of `float` class), not primitives like in Java (double is primitive, fixed 64-bit). This means they have methods (e.g., .is_integer()) and garbage collection, but slight overhead.

6. **Memory and Performance**: Floats take 24 bytes typically. For exact decimals (e.g., money in your app), use `from decimal import Decimal` to avoid binary floating-point issues.

Experiment in shell: `>>> 1.5 * 2` → 3.0.

## Syntax
- Basic: `pi = 3.14159`, `negative = -2.5`, `sci = 1.23e-4` (0.000123)
- Conversion: `num = float(input("Enter float: "))`, `whole = float(42)` → 42.0
- In expressions: `result = (3.5 + 1.2) * 2.0 ** 2 / 4.0` → 3.925
- Rounding: `round(3.14159, 2)` → 3.14

No underscores in floats like 1_000.5 (invalid); use for readability in code comments.

## Sample Code Example
Let's build a simple area calculator:

```python
# Step 1: Define floats
radius = 5.0  # positive
height = 10.5
pi = 3.14159  # approximate
negative = -2.3  # for demo

# Step 2: Operations
area = pi * radius ** 2  # 78.53975
volume = area * height  # 825.667375
abs_val = abs(negative)  # 2.3
div = 10.0 / 3  # 3.333...
floor_div = 10.0 // 3  # 3.0 (float result)
rounded = round(volume, 2)  # 825.67

# Step 3: Print
print("Area:", area)
print("Volume:", volume)
print(f"Rounded: {rounded}, Div: {div}")

# Step 4: Input and conversion
user = input("Enter height: ")  # e.g., "4.5"
h = float(user)
new_volume = area * h
print("New Volume:", new_volume)

# Step 5: Precision demo
print(0.1 + 0.2)  # 0.30000000000000004
from decimal import Decimal
precise = Decimal('0.1') + Decimal('0.2')  # Decimal('0.3')
print(precise)  # 0.3
```

Save as floats.py and run. If input not number, use try/except (later concept).

## Methods
Floats inherit from numbers.Number; methods with one-line def and example:

- `is_integer()`: Checks if float is integral (no decimal). Example: `(5.0).is_integer()` → True, `(5.1).is_integer()` → False
- `hex()`: Returns hexadecimal string. Example: `(255.0).hex()` → '0x1.fe00000000000p+7'
- `as_integer_ratio()`: Returns (numerator, denominator) tuple. Example: `(0.5).as_integer_ratio()` → (1, 2)
- `fromhex(s)`: Class method to create float from hex string. Example: `float.fromhex('0x1.8p+0')` → 1.5
- `conjugate()`: Returns self (complex compatibility). Example: `(3.14).conjugate()` → 3.14
- `real`: Returns self. Example: `(2.5).real` → 2.5
- `imag`: Returns 0.0. Example: `(2.5).imag` → 0.0
- `__abs__()`: Absolute value. Example: `abs(-3.14)` → 3.14
- `__floor__()`: Floor via math.floor. Example: `math.floor(3.9)` → 3
- `__ceil__()`: Ceiling via math.ceil. Example: `math.ceil(3.1)` → 4

## 10 Interview Questions
1. What is floating-point precision, and why does 0.1 + 0.2 not equal 0.3?
2. How do you represent scientific notation in floats?
3. What is the difference between float and Decimal?
4. Explain why floats are non-primitive in Python.
5. How does Python handle float division with integers?
6. What is the maximum precision of floats?
7. How to round a float to 2 decimal places?
8. What does is_integer() do, and when is it useful?
9. Explain as_integer_ratio() with an example.
10. Why use float instead of int for measurements in your app?

## 10 Coding Interview Questions
1. Write code to round a float to n decimal places without round().
2. Check if a float is close to an integer (tolerance 0.001).
3. Convert float to fraction (e.g., 0.75 → 3/4).
4. Calculate area of circle with pi approximation.
5. Find average of list of floats.
6. Implement simple interest calculator (principal * rate * time / 100).
7. Handle floating-point comparison with epsilon (e.g., if a == b within 1e-9).
8. Sort list of floats in descending order.
9. Find max/min in list of floats without max/min functions.
10. Simulate dice roll with random floats (0-1) to get 1-6.

## Links for YouTube Reference Videos
1. "Python Floats for Beginners" by Corey Schafer (https://www.youtube.com/watch?v=khKv-8q7YmY&t=300s) - 8min on basics, operations, precision issues (watch 0:00-5:00 first).
2. "Floating Point Numbers in Python" by Programming with Mosh (https://www.youtube.com/watch?v=_uQrJ0TkZlc&t=600s) - Explains with analogies, common errors (full 10min video).
3. "Python Tutorial: Float Data Type" by freeCodeCamp (https://www.youtube.com/watch?v=eoO3Jf-h5uM) - 5min simple intro with code along.
4. "Why 0.1 + 0.2 != 0.3 in Python" by Socratica (https://www.youtube.com/watch?v=PZRI1IfStY0) - 7min on precision, must-watch for novices.
5. "Decimal vs Float in Python" by Telusko (https://www.youtube.com/watch?v=9f4rvaYcJHI&t=200s) - 6min comparison, useful for your e-commerce prices (watch with code editor open).

These videos are beginner-level—watch one per day, pause to try code.