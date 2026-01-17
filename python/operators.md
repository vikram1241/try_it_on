# python_operators.md

## Definition of Operators
**Operators** in Python are special symbols that perform operations on one or more values (operands).  
They allow you to do math, compare values, combine text, check conditions, assign values, and more.

For complete beginners with zero knowledge:  
Think of operators like signs on a calculator or traffic signs:  
- `+` = "add"  
- `>` = "is greater than"  
- `=` = "put this value into the box"  

Operators are the tools that let your program **do things** with data (numbers, text, booleans, etc.).

In your project:
- Calculate total cart price: `total = price * quantity`
- Check if size fits: `if user_size in available_sizes`
- Compare prices: `if price < 1000: show_discount()`
- Combine strings: `full_name = first + " " + last`

Without operators, you couldn’t do any calculations or decisions.

## What and Why Operators
**What**: Symbols that tell Python to perform actions like addition, comparison, assignment, etc.

**Why we need operators**:
- Perform math (add prices, calculate discounts)
- Make decisions (if age > 18, allow purchase)
- Compare values (check if size matches)
- Combine data (build full product description)
- Assign values to variables
- Work with booleans (and/or/not for complex conditions)

Operators are the "verbs" of programming — they make things happen.

## Detailed Explanation How Operators Work in Python (for Absolute Beginners)
Python has several categories of operators. We'll cover the most important ones for beginners.

### 1. Arithmetic Operators (Math)
| Operator | Meaning                  | Example             | Result |
|----------|--------------------------|---------------------|--------|
| `+`      | Addition                 | `5 + 3`             | 8      |
| `-`      | Subtraction              | `10 - 4`            | 6      |
| `*`      | Multiplication           | `4 * 3`             | 12     |
| `/`      | Division (always float)  | `10 / 3`            | 3.333… |
| `//`     | Floor division (integer) | `10 // 3`           | 3      |
| `%`      | Modulo (remainder)       | `10 % 3`            | 1      |
| `**`     | Exponent (power)         | `2 ** 3`            | 8      |

```python
price = 999.99
quantity = 2
total = price * quantity          # 1999.98
discount = total * 0.1            # 199.998
final = total - discount          # 1799.982
print(round(final, 2))            # 1799.98
```

### 2. Comparison Operators (Make Decisions)
Return `True` or `False`

| Operator | Meaning                  | Example            | Result |
|----------|--------------------------|--------------------|--------|
| `==`     | Equal to                 | `5 == 5`           | True   |
| `!=`     | Not equal to             | `5 != 3`           | True   |
| `>`      | Greater than             | `10 > 7`           | True   |
| `<`      | Less than                | `3 < 5`            | True   |
| `>=`     | Greater than or equal    | `18 >= 18`         | True   |
| `<=`     | Less than or equal       | `16 <= 18`         | True   |

```python
age = 25
if age >= 18:
    print("You can buy")
else:
    print("Not allowed")
```

### 3. Logical Operators (Combine Conditions)
| Operator | Meaning                  | Example                             | Result |
|----------|--------------------------|-------------------------------------|--------|
| `and`    | Both must be True        | `True and False`                    | False  |
| `or`     | At least one True        | `True or False`                     | True   |
| `not`    | Reverse                  | `not True`                          | False  |

```python
in_stock = True
size_available = True
can_buy = in_stock and size_available   # True
show_button = can_buy or is_premium     # True if either
```

### 4. Assignment Operators (Short form)
| Operator | Meaning                  | Example             | Same as        |
|----------|--------------------------|---------------------|----------------|
| `=`      | Assign                   | `x = 5`             |                |
| `+=`     | Add and assign           | `x += 3`            | `x = x + 3`    |
| `-=`     | Subtract and assign      | `x -= 2`            | `x = x - 2`    |
| `*=`     | Multiply and assign      | `x *= 4`            | `x = x * 4`    |
| `/=`     | Divide and assign        | `x /= 2`            | `x = x / 2`    |

```python
total = 0
total += 999.99     # total = 999.99
total += 499.50     # total = 1499.49
```

### 5. Membership Operators (Check if in collection)
| Operator | Meaning                  | Example                     | Result |
|----------|--------------------------|-----------------------------|--------|
| `in`     | Is value in sequence?    | `"shirt" in cart`           | True/False |
| `not in` | Is value not in?         | `"shoes" not in cart`       | True/False |

```python
cart = ["shirt", "cap"]
print("cap" in cart)         # True
print("shoes" not in cart)   # True
```

### 6. Identity Operators (Check if same object)
| Operator | Meaning                  | Example                     |
|----------|--------------------------|-----------------------------|
| `is`     | Same object in memory?   | `x is y`                    |
| `is not` | Not same object?         | `x is not y`                |

Used rarely in beginner code — mostly for `None`, `True`, `False`.

```python
a = [1,2]
b = a            # same list
c = [1,2]        # different list with same content

print(a is b)     # True
print(a is c)     # False
print(a == c)     # True (same content)
```

## Sample Code Example (Practical for your project)
```python
# --- Mini price calculator & stock checker ---

# Arithmetic
price = 999.99
quantity = 2
subtotal = price * quantity           # 1999.98
discount_percent = 10
discount_amount = subtotal * (discount_percent / 100)  # 199.998
total = subtotal - discount_amount    # 1799.982
final_total = round(total, 2)         # 1799.98

print("Final Total: ₹", final_total)

# Comparison & Logical
age = 17
has_id = True
can_buy = (age >= 18) and has_id      # False
print("Can buy?", can_buy)

# Membership
available_sizes = [38, 40, 42]
user_size = 40
if user_size in available_sizes:
    print("Size available!")
else:
    print("Size not available.")

# Assignment shortcuts
total_items = 0
total_items += 1     # add shirt
total_items += 1     # add cap
print("Items in cart:", total_items)

# Identity example (rare for beginners)
cart1 = ["shirt"]
cart2 = cart1        # same cart
cart3 = ["shirt"]    # different cart

print(cart1 is cart2)   # True
print(cart1 is cart3)   # False
print(cart1 == cart3)   # True (same content)
```

Run this — change values and see how operators control logic and math.

## 10 Interview Questions (Beginner Level)
1. What are the different types of operators in Python?
2. What is the difference between `=` and `==`?
3. Explain `/` vs `//` with example.
4. What do `and`, `or`, and `not` do?
5. What is the modulo operator `%` used for?
6. Explain the difference between `is` and `==`.
7. What does `in` operator do? Give example with list and string.
8. How do assignment operators like `+=` work?
9. What is operator precedence? (which runs first: * or +?)
10. Give an example of using logical operators in a real condition.

## 10 Coding Interview Questions (Beginner Level)
1. Calculate final price after 15% discount using operators.
2. Check if user age is between 18 and 60 using comparison operators.
3. Use `in` to check if "shirt" is in cart list.
4. Add 5 items to cart using `+=` shortcut.
5. Print "Even" if number % 2 == 0 else "Odd".
6. Check if user is eligible: age >= 18 AND has_money OR is_premium.
7. Calculate area of circle: pi * r ** 2 (use ** operator).
8. Use `not` to check if item NOT in cart.
9. Compare two prices and print the cheaper one.
10. Use logical operators to decide if to show "Free Shipping" (total >= 1000 OR premium user).

## Links for YouTube Reference Videos
1. "Python Operators for Beginners" – Corey Schafer  
   https://www.youtube.com/watch?v=v5MR5JnKcZI (full 25min) — Best beginner video, covers all types clearly.

2. "Operators in Python – Arithmetic, Comparison, Logical" – Programming with Mosh  
   https://www.youtube.com/watch?v=6iF8Xb7Z3wQ&t=600s (first 15 minutes) — Simple & practical.

3. "Python Operators Tutorial" – freeCodeCamp  
   https://www.youtube.com/watch?v=PWdPLZvdO_I (watch operators section) — Visual examples.

4. "Understanding Python Operators" – Telusko  
   https://www.youtube.com/watch?v=uoS7Yg3l3hA – 12min live coding all operators.

5. "Comparison & Logical Operators in Python" – Socratica  
   https://www.youtube.com/watch?v=PZRI1IfStY0 – 10min, great for beginners.

**Tip for Novices**  
Operators are the "action words" of code.  
Practice:  
1. `print(5 + 3)` → 8  
2. `print(10 / 3)` → 3.333  
3. `print(10 // 3)` → 3  
4. `print(10 % 3)` → 1  
5. `print(2 ** 3)` → 8  
6. Try comparisons: `print(5 > 3)` → True  
7. Combine: `print(age >= 18 and has_money)`  

This is how you'll calculate totals, check sizes, apply discounts, and make decisions in your app.

Next file? Say: "next: python_functions.md" or any other (python_oop_classes.md, python_file_io.md, python_exceptions.md, etc.)