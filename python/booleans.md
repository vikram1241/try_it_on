# python_booleans.md

## Definition of Boolean
A **boolean** in Python is a data type that can have only two possible values: `True` or `False`.  
It is used to represent logical states — something is either true or not true.

For complete beginners with zero knowledge:  
Think of a boolean like a light switch:  
- `True` = light is ON  
- `False` = light is OFF  

There is no middle state — only these two options. Booleans are named after mathematician George Boole, who invented Boolean algebra (the logic behind computers).

## What and Why Booleans
**What**: Booleans store yes/no, on/off, correct/incorrect answers.

**Why we need them**:
- Control decisions in code ("if this is true, do that")
- Check conditions (is user logged in? is product in stock? is size correct?)
- Make comparisons (is age > 18?)
- Control loops (repeat while something is true)
- Store flags/states (has_discount = True)

In your project (wearables e-commerce with virtual try-on):
- `is_logged_in = True` — show checkout button
- `in_stock = False` — show "Out of Stock" message
- `fit_perfect = True` — allow "Add to Cart"
- `has_fabric_booklet = False` — show "Request Booklet" button

Booleans are the "decision makers" of every program.

## Detailed Explanation How Booleans Work in Python (for Absolute Beginners)
Step-by-step for someone who has never coded:

1. **Only Two Values**  
   `True` and `False` are built-in keywords (must be capitalized — `true` or `TRUE` will give error).

2. **Creation**  
   ```python
   is_adult = True
   has_discount = False
   product_in_stock = True
   ```

3. **Comparisons Create Booleans**  
   When you compare things, Python gives you a boolean result:
   ```python
   age = 20
   print(age > 18)       # True
   print(age == 18)      # False
   print(age < 15)       # False
   print(age != 25)      # True
   ```

4. **Logical Operators** (combine booleans)
   - `and`: both must be True → True
   - `or`: at least one True → True
   - `not`: reverses (True → False, False → True)

   ```python
   has_money = True
   has_card = False

   can_buy = has_money or has_card      # True (one is enough)
   can_enter = age >= 18 and has_ticket  # depends on both
   is_blocked = not can_buy             # False
   ```

5. **Truthy & Falsy Values** (very important for beginners)  
   Python treats many values as "True" or "False" in conditions:
   - Falsy (treated as False): `False`, `0`, `0.0`, `""` (empty string), `[]` (empty list), `None`
   - Truthy (treated as True): everything else (non-zero numbers, non-empty strings/lists, True)

   ```python
   if 0:          # False — won't run
       print("Zero")
   if "hello":    # True — will run
       print("Non-empty string")
   if []:         # False
       print("Empty list")
   ```

6. **Boolean in Conditions (if statements – preview)**  
   ```python
   is_adult = True
   if is_adult:
       print("You can buy this product")
   else:
       print("Sorry, age restricted")
   ```

7. **Common Pitfalls for Novices**
   - Writing `true` instead of `True` → NameError
   - Using `=` (assignment) instead of `==` (comparison) in conditions
   - Forgetting `:` after `if` or `else`
   - Thinking `None` is same as `False` (it's falsy but different)

8. **Type Checking**  
   ```python
   print(type(True))     # <class 'bool'>
   print(isinstance(1, bool))   # False (1 is int, even though truthy)
   ```

## Syntax
```python
# Direct assignment
is_logged_in = True
out_of_stock = False

# From comparisons
can_checkout = age >= 18 and cart_total > 0
has_size = selected_size in available_sizes  # later topic

# Logical combinations
premium_user = is_premium or has_voucher
show_button = is_logged_in and not out_of_stock
```

## Sample Code Example (Practical for your project)
```python
# --- Mini login & stock checker for your app ---

# Variables
username = "vikram"
password_correct = True
age = 22
is_premium = False
product_in_stock = True
has_discount = True
cart_has_items = True

# Boolean logic
can_login = password_correct
is_adult = age >= 18
can_buy = is_adult and product_in_stock and cart_has_items
show_checkout = can_buy and (is_premium or has_discount)
show_booklet_button = product_in_stock and not is_premium  # example rule

# Print decisions
print("Can login?", can_login)                # True
print("Is adult?", is_adult)                  # True
print("Can buy?", can_buy)                    # True
print("Show checkout button?", show_checkout) # True (has_discount)
print("Show fabric booklet option?", show_booklet_button)  # False

# Falsy example
no_items = False
if no_items:
    print("Cart is empty!")
else:
    print("Cart has items → proceed")  # this prints
```

Run this — change values (e.g., `product_in_stock = False`) and see how decisions change.

## Methods (Booleans have very few – they are simple)
Booleans inherit from `int` (True = 1, False = 0 internally), so they have these:

- `bit_length()`: Returns 1 for True, 0 for False. Example: `True.bit_length()` → 1
- `conjugate()`: Returns self. Example: `True.conjugate()` → True
- `real`: Returns self. Example: `True.real` → True
- `imag`: Returns 0. Example: `False.imag` → 0

Most of the time, you don't use methods on booleans — you use them in conditions and logic.

## 10 Interview Questions (Beginner Level)
1. What are the two possible values of a boolean in Python?
2. How do you write True and False? (capitalization matters?)
3. What is the difference between `True` and `"True"`?
4. Explain `and`, `or`, and `not` with examples.
5. What values are considered falsy in Python?
6. Why is `True` actually equal to 1 and `False` to 0 internally?
7. What happens if you do `if "hello":`?
8. How do you check if two conditions are both true?
9. What is the output of `not False`?
10. Give an example of using boolean in a real app (like your project).

## 10 Coding Interview Questions (Beginner Level)
1. Create variables `is_adult`, `has_money`, `is_weekend` and print whether person can go to movie (adult OR money AND weekend).
2. Ask user for age and print "Adult" if age >= 18 else "Minor".
3. Check if a number is positive, negative, or zero using booleans.
4. Create `in_stock` and `has_size` — print "Can buy" only if both are True.
5. Use `not` to check if user is NOT logged in.
6. Print "Eligible for discount" if user is premium OR order > 1000.
7. Check if cart is empty (len(cart) == 0) and print message.
8. Create `is_prime_user` = True if user has bought > 5 times (use boolean).
9. Use boolean to decide if to show "Out of Stock" label.
10. Combine three conditions: adult AND logged in AND in_stock → allow checkout.

## Links for YouTube Reference Videos
1. "Python Booleans – True or False Explained" – Corey Schafer  
   https://www.youtube.com/watch?v=9f4rvaYcJHI&t=600s (watch 10:00–18:00) – Clear, beginner-friendly.

2. "Python Boolean Logic for Beginners" – Programming with Mosh  
   https://www.youtube.com/watch?v=_uQrJ0TkZlc&t=900s (first 12 minutes) – Great analogies, light switch example.

3. "Understanding True and False in Python" – freeCodeCamp  
   https://www.youtube.com/watch?v=eoO3Jf-h5uM&t=1800s (watch 30:00–40:00) – Shows truthy/falsy with examples.

4. "Python Logical Operators (and, or, not)" – Telusko  
   https://www.youtube.com/watch?v=uoS7Yg3l3hA – 8min, very simple with live coding.

5. "Truthy and Falsy Values in Python" – Socratica  
   https://www.youtube.com/watch?v=PZRI1IfStY0 – 6min, must-watch for beginners to avoid confusion.

**Tip for Novices**  
Booleans seem simple, but truthy/falsy trips up many beginners.  
After watching videos, open Python shell and try:  
`if 0: print("Zero")` → nothing prints  
`if "": print("Empty")` → nothing  
`if "hello": print("Non-empty")` → prints  

Type along — change values and see how decisions change. This is key for your app's "if in stock" and "if size matches" logic!

Next file? Say: "next: python_lists.md" or any name (python_tuples.md, python_dictionaries.md, python_loops.md, etc.)