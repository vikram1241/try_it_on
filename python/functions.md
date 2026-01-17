# python_functions.md

## Definition of Function
A **function** in Python is a reusable block of code that performs a specific task.  
It has a name, can take inputs (parameters), does some work, and often returns an output.

For complete beginners with zero knowledge:  
Think of a function like a recipe or a vending machine:  
- You give it inputs (coins + choice)  
- It does work (makes the snack)  
- It gives you output (the snack)  
- You can use the same machine many times with different choices  

Instead of writing the same code again and again, you write it once in a function and call it whenever needed.

Examples from your project:
- `calculate_total(cart)` — adds up prices in cart
- `create_avatar(photos, measurements)` — generates 3D avatar
- `send_booklet_request(user_address)` — handles fabric sample request

Functions make your code organized, reusable, shorter, and easier to fix.

## What and Why Functions
**What**: Functions let you group code, give it a name, and reuse it.

**Why we need functions**:
- Avoid repeating code (DRY – Don't Repeat Yourself)
- Make code easier to read and understand
- Break big problems into small, manageable pieces
- Easier to test and debug (fix one function, not the whole program)
- Reuse code across your project (e.g., format prices in many places)
- Pass data in (parameters) and get results back (return)

In your app:
- One function to validate size input
- One to calculate discount
- One to generate Gen AI texture preview
- One to send email for booklet request

Without functions, your code would be a long, messy list of instructions — hard to maintain.

## Detailed Explanation How Functions Work in Python (for Absolute Beginners)
Step-by-step:

1. **Defining a Function** (creating it)
   ```python
   def greet():
       print("Hello, welcome to the app!")
   ```
   - `def` keyword
   - Function name (follow variable rules: lowercase_with_underscores)
   - Parentheses `()`
   - Colon `:`
   - Indented block — the code that runs when function is called

2. **Calling a Function** (using it)
   ```python
   greet()   # prints "Hello, welcome to the app!"
   ```

3. **Parameters** (inputs)
   ```python
   def greet_user(name):
       print("Hello,", name, "! Welcome!")
   
   greet_user("Vikram")   # Hello, Vikram ! Welcome!
   greet_user("Priya")    # Hello, Priya ! Welcome!
   ```

   - Parameters go inside `()`
   - You can have multiple: `def add(a, b):`

4. **Return Statement** (output)
   ```python
   def add(a, b):
       result = a + b
       return result
   
   total = add(5, 3)   # total = 8
   print(total)        # 8
   ```

   - `return` sends value back to caller
   - Stops function execution
   - If no return → function returns `None` (special value meaning nothing)

5. **Default Parameters**
   ```python
   def greet(name="Guest"):
       print("Hello,", name)
   
   greet()         # Hello, Guest
   greet("Vikram") # Hello, Vikram
   ```

6. **Keyword Arguments**
   ```python
   def introduce(name, age, city):
       print(f"{name} is {age} from {city}")
   
   introduce(age=25, name="Vikram", city="Airoli")  # order doesn't matter
   ```

7. **Variable Number of Arguments**
   - `*args` (multiple positional args → tuple)
   ```python
   def total_price(*prices):
       return sum(prices)
   
   print(total_price(100, 200, 300))  # 600
   ```

   - `**kwargs` (multiple keyword args → dictionary)
   ```python
   def user_info(**details):
       print(details)
   
   user_info(name="Vikram", age=25, city="Airoli")
   # {'name': 'Vikram', 'age': 25, 'city': 'Airoli'}
   ```

8. **Scope** (where variables live)
   - Variables inside function → local (disappear after function ends)
   - Variables outside → global (can be read, but to change use `global` keyword – avoid if possible)

9. **Common Pitfalls for Novices**
   - Forgetting colon `:` after `def`
   - Wrong indentation of function body
   - Calling function before defining it (order matters)
   - Not returning value when needed
   - Modifying mutable default arguments (dangerous – avoid defaults like lists/dicts)

## Syntax
```python
# Basic
def function_name():
    # code here

# With parameters & return
def function_name(param1, param2=default):
    # do work
    return some_value

# Call it
result = function_name(value1, value2)
```

## Sample Code Example (Practical for your project)
```python
# --- Mini functions for your wearables app ---

# Function 1: Calculate total price with discount
def calculate_total(cart_prices, discount=0):
    total = sum(cart_prices)
    final = total * (1 - discount)
    return round(final, 2)

# Function 2: Check if size is available
def is_size_available(user_size, available_sizes):
    return user_size in available_sizes

# Function 3: Generate welcome message
def welcome_user(name="Guest", is_premium=False):
    msg = f"Welcome, {name}!"
    if is_premium:
        msg += " Enjoy 10% off as premium member!"
    return msg

# Function 4: Format product info
def format_product(name, price, sizes):
    size_str = ", ".join(map(str, sizes))
    return f"{name} - ₹{price} | Sizes: {size_str}"

# Using the functions
cart = [999.99, 499.50, 1999.00]           # shirt, cap, watch
total = calculate_total(cart, discount=0.1) # 10% off
print("Total after discount:", total)

available = [38, 40, 42]
print("Size 40 available?", is_size_available(40, available))

print(welcome_user("Vikram", is_premium=True))

product_info = format_product("Blue Shirt", 999.99, [38, 40, 42])
print(product_info)
```

Run this — change inputs, see how functions make code clean and reusable.

## 10 Interview Questions (Beginner Level)
1. What is a function in Python?
2. Why do we use functions instead of writing code directly?
3. What is the difference between parameters and arguments?
4. What does `return` do? What if a function has no return?
5. Explain default parameters with example.
6. What are `*args` and `**kwargs`?
7. What is function scope? What is local vs global variable?
8. Can a function call itself? (hint: recursion – later topic)
9. How do you call a function with keyword arguments?
10. What happens if you forget `()` when calling a function?

## 10 Coding Interview Questions (Beginner Level)
1. Write a function to add two numbers and return the sum.
2. Create a function that takes name and prints "Hello, name!".
3. Write a function to calculate area of rectangle (length × width).
4. Make a function that checks if number is even or odd.
5. Create function to find maximum of three numbers.
6. Write function that takes list of prices and returns total.
7. Make greeting function with default name="Guest".
8. Function to check if size is in available sizes list.
9. Create function to format price with ₹ symbol and 2 decimals.
10. Write function that takes **kwargs and prints user profile.

## Links for YouTube Reference Videos
1. "Python Functions for Beginners" – Corey Schafer  
   https://www.youtube.com/watch?v=9Os0o3wzS_I (full 20min) – Best beginner video, very thorough and clear.

2. "Functions in Python – Tutorial" – Programming with Mosh  
   https://www.youtube.com/watch?v=9f4rvaYcJHI&t=2400s (first 15 minutes) – Simple, step-by-step with examples.

3. "Python Functions Explained" – freeCodeCamp  
   https://www.youtube.com/watch?v=PWdPLZvdO_I (watch functions section) – Visual and practical.

4. "*args and **kwargs in Python" – Telusko  
   https://www.youtube.com/watch?v=uoS7Yg3l3hA – 10min, live coding of variable arguments.

5. "Understanding Functions & Return in Python" – Socratica  
   https://www.youtube.com/watch?v=PZRI1IfStY0 – 10min, great for return and scope.

**Tip for Novices**  
Functions are like mini-programs inside your program.  
Practice:  
1. Write `def say_hello(): print("Hi!")`  
2. Call it: `say_hello()`  
3. Add parameter: `def say_hello(name): print("Hi", name)`  
4. Call with different names  
5. Add return: `def add(a,b): return a+b`  
6. Use result = add(5,3); print(result)

This is how you'll write clean, reusable code for calculating totals, checking sizes, generating avatars, etc.

Next file? Say: "next: python_oop_classes.md" or any other (python_oop_inheritance.md, python_file_io.md, python_exceptions.md, etc.)