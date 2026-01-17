# python_conditionals.md

## Definition of Conditional Statements
**Conditional statements** (also called **if statements**, **decision-making**, or **control flow**) in Python allow your program to make decisions and run different blocks of code based on whether a condition is `True` or `False`.

For complete beginners with zero knowledge:  
Think of conditional statements like a traffic light or a door guard:  
- The program asks a question: "Is it raining?"  
- If yes (`True`) → take umbrella (do one thing)  
- If no (`False`) → don't take umbrella (do another thing)  

This is how your program becomes "smart" — it reacts differently depending on the situation.

In your project:
- "If user is logged in → show checkout button"
- "If size is in stock → allow add to cart"
- "If total > 1000 → apply discount"
- "If fabric booklet requested → send email"

Conditionals make your app respond intelligently to user data.

## What and Why Conditionals
**What**: Conditionals let code choose which instructions to execute based on boolean conditions (`True`/`False`).

**Why we need them**:
- Programs need to make decisions (not always do the same thing)
- Handle different user inputs or situations
- Validate data (e.g., age ≥ 18)
- Control program flow (show error if invalid size)
- Make apps interactive and user-friendly

Without conditionals, your program would be a straight line — no choices, no intelligence.

## Detailed Explanation How Conditionals Work in Python (for Absolute Beginners)
Step-by-step:

1. **Basic if statement**  
   ```python
   is_raining = True

   if is_raining:
       print("Take umbrella!")   # runs only if True
   ```

   - `if` keyword
   - Condition (expression that gives True/False)
   - Colon `:` at end
   - Indented block (4 spaces or 1 tab) — very important!

2. **if-else** (two choices)
   ```python
   age = 16

   if age >= 18:
       print("You can buy this product")
   else:
       print("Sorry, age restricted")
   ```

3. **if-elif-else** (multiple choices)
   ```python
   score = 85

   if score >= 90:
       print("Grade A")
   elif score >= 80:
       print("Grade B")
   elif score >= 70:
       print("Grade C")
   else:
       print("Grade D or Fail")
   ```

   - `elif` means "else if"
   - Only one block runs
   - Order matters — first true condition wins

4. **Nested if** (if inside if)
   ```python
   is_logged_in = True
   has_money = False

   if is_logged_in:
       if has_money:
           print("Proceed to checkout")
       else:
           print("Add money to wallet")
   else:
       print("Please login first")
   ```

5. **Conditions (what can go inside if)**
   - Comparisons: `==` (equal), `!=` (not equal), `>`, `<`, `>=`, `<=`
   - Boolean variables: `if is_adult:`
   - Truthy/Falsy values: `if name:` (True if non-empty string)
   - Logical operators: `and`, `or`, `not`
   ```python
   if age >= 18 and has_id:
       print("Allowed")
   ```

6. **Common Comparison Operators**
   - `==` : equal to (don't confuse with `=` assignment)
   - `!=` : not equal
   - `>` , `<` , `>=` , `<=`
   - `is` : checks identity (same object) — rare for beginners
   - `in` : membership (for lists, strings, sets, dicts)

7. **Common Pitfalls for Novices**
   - Using `=` instead of `==`: `if age = 18:` → SyntaxError or wrong logic
   - Wrong indentation: code must be indented under `if`/`else`
   - Forgetting colon `:` after condition
   - Using `elif` after `else` (wrong order)
   - Comparing strings case-sensitively: `"Mumbai" == "mumbai"` → False

8. **Ternary Operator** (short if-else – one line)
   ```python
   status = "Adult" if age >= 18 else "Minor"
   print(status)
   ```

## Syntax
```python
# Basic if
if condition:
    # indented code runs if True

# if-else
if condition:
    # True block
else:
    # False block

# if-elif-else
if condition1:
    pass
elif condition2:
    pass
else:
    pass
```

**Indentation rule**: All code under `if`/`elif`/`else` must be indented the same amount (usually 4 spaces). Python uses indentation instead of `{}` braces.

## Sample Code Example (Practical for your project)
```python
# --- Mini size & stock checker for your wearables app ---

# Step 1: User inputs
user_size = 40
available_sizes = {38, 40, 42}
in_stock = True
is_premium = False
cart_total = 2500

# Step 2: Check size availability
if user_size in available_sizes:
    print("Size", user_size, "is available!")
else:
    print("Sorry, size", user_size, "not available.")

# Step 3: Complex condition for checkout
if in_stock and user_size in available_sizes:
    if cart_total >= 2000 or is_premium:
        print("Eligible for free shipping!")
    else:
        print("Add more items for free shipping.")
    print("Proceed to checkout")
else:
    print("Cannot checkout – item out of stock or wrong size.")

# Step 4: Ternary example
discount_message = "10% off!" if is_premium else "No discount"
print(discount_message)

# Step 5: Booklet request logic
booklet_requested = True
if booklet_requested and in_stock:
    print("Fabric booklet will be sent with order.")
```

Run this — change `user_size`, `in_stock`, etc., and see different outputs.

## Keywords & Operators Used
- `if`, `elif`, `else`
- Comparison: `==`, `!=`, `>`, `<`, `>=`, `<=`
- Logical: `and`, `or`, `not`
- Membership: `in`, `not in`
- Identity: `is`, `is not` (advanced, rarely used early)

## 10 Interview Questions (Beginner Level)
1. What is the purpose of conditional statements in Python?
2. Explain the difference between `if` and `elif`.
3. What happens if you forget the colon `:` after `if`?
4. Why is indentation important in Python conditionals?
5. What is the difference between `=` and `==`?
6. Explain truthy and falsy values with examples.
7. How does `and` and `or` work in conditions?
8. What is a ternary operator? Give example.
9. Can you have `else` without `if`? Why or why not?
10. Give a real-life example of using `if-elif-else`.

## 10 Coding Interview Questions (Beginner Level)
1. Ask user for age and print "Adult" if >= 18 else "Minor".
2. Check if a number is positive, negative, or zero.
3. Take two numbers and print the larger one.
4. Check if user entered "yes" or "no" (case insensitive).
5. Give discount if total > 1000 (print "Discount applied").
6. Check if size is in available sizes set.
7. Print "Eligible" if age >= 18 and has_id is True.
8. Use ternary to assign "Pass" or "Fail" based on score >= 40.
9. Check if cart_total >= 500 for free shipping.
10. Print "Out of Stock" if in_stock is False.

## Links for YouTube Reference Videos
1. "Python If Statements for Beginners" – Corey Schafer  
   https://www.youtube.com/watch?v=DZwmZ8Usvnk (full 15min) – Best beginner video, very clear.

2. "If, Elif, Else in Python" – Programming with Mosh  
   https://www.youtube.com/watch?v=4z7J_2M1b0A (first 12 minutes) – Simple, step-by-step.

3. "Python Conditionals Tutorial" – freeCodeCamp  
   https://www.youtube.com/watch?v=6iF8Xb7Z3wQ (watch conditionals section) – Visual examples.

4. "Understanding if-elif-else in Python" – Telusko  
   https://www.youtube.com/watch?v=5dtQJq3J0cA – 10min, live coding decisions.

5. "Truthy and Falsy Values + Conditionals" – Socratica  
   https://www.youtube.com/watch?v=9f4rvaYcJHI – 8min, explains why `if ""` is False.

**Tip for Novices**  
Conditionals are where your program starts "thinking".  
Practice:  
1. Write `if True: print("This runs")`  
2. Change to `if False:` — nothing prints  
3. Add `else:` block  
4. Try `if age > 18:` with different ages  
5. Combine with `and`/`or`  

This is the heart of making your app smart — "if this, then show checkout".

Next file? Say: "next: python_loops.md" or any other (python_functions.md, python_oop_classes.md, etc.)