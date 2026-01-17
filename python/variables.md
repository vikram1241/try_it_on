# python_variables.md

## Definition of Variable
A variable in Python is a named storage location in your computer's memory that holds a value (like a number, text, or list). It acts like a labeled box where you can put data, change it later, or use it in calculations. In programming, variables let you store information so your program can remember and work with it.

For complete beginners: Imagine you're cooking and need to keep track of "sugar = 2 spoons". In Python, `sugar = 2` creates a variable named `sugar` that holds the value 2. You can later say `sugar = sugar + 1` to add more.

## What and Why Variables
**What**: Variables are names you give to pieces of data so you can refer to them easily. Python variables can hold almost anything: numbers, text, lists, or even complex objects.

**Why**: Without variables, every time you want to use a value (like a user's height in your virtual try-on app), you'd have to write the number again and again. Variables make code reusable, readable, and changeable. For example:
- Store user measurements once: `height = 175`
- Use it many times: calculate BMI, scale avatar, recommend sizes
- Change it easily if user updates: `height = 178`

Variables are the foundation of every program. Without them, you can't build anything useful—like saving a user's avatar data or product prices in your e-commerce app.

## Detailed Explanation How Variables Work in Python (for Absolute Beginners)
Step-by-step guide:

1. **Creation (Assignment)**: Use the `=` sign to create and set a variable.  
   Example: `age = 25`  
   This tells Python: "Create a box called age and put the number 25 inside it."

2. **Naming Rules** (very important for beginners):
   - Must start with letter (a-z, A-Z) or underscore (_)
   - Can contain letters, numbers, underscore (no spaces or special chars like @, #)
   - Case-sensitive: `Age` and `age` are different variables
   - Don't use Python keywords (if, for, while, class, def, etc.)
   - Good names: `user_height`, `total_price`, `is_adult` (descriptive)
   - Bad names: `x`, `temp`, `a1` (not meaningful)

3. **Dynamic Typing**: Python figures out the type automatically—no need to say "this is a number".  
   Example: `x = 10` (x is int), then `x = "hello"` (now x is string). This is flexible but can cause mistakes if you're not careful.

4. **Memory and References**: When you do `a = 5`, Python creates an integer object 5 in memory and points the name `a` to it.  
   Then `b = a` — `b` points to the same object (not a copy).  
   If you change `a = 6`, `b` still points to 5 (because integers are immutable).

5. **Multiple Assignment**: `x, y, z = 1, 2, 3` or `a = b = 0`

6. **Deletion**: `del x` removes the variable (frees memory if no other references).

7. **Scope**: Variables inside functions are local (only exist inside function) unless declared `global`.

8. **Common Pitfalls for Novices**:
   - Forgetting quotes for text: `name = John` (error) → `name = "John"`
   - Using variable before assignment: `print(age)` before `age = 25` → NameError
   - Typos in variable names: `heigth` vs `height`
   - Reusing names accidentally overwrites values

In your project: Variables will store user measurements (`chest = 90`), avatar data, product prices, cart items, etc.

## Syntax
- Basic: `variable_name = value`
- Examples:
  ```python
  name = "Vikram"           # string
  age = 25                  # integer
  height = 175.5            # float
  is_student = True         # boolean
  items_in_cart = 3         # integer for e-commerce
  user_measurements = {"chest": 90, "waist": 80}  # dictionary (later topic)
  ```

- Reassignment: `age = age + 1` or `age += 1` (same result)
- Swap: `a, b = b, a` (no temp variable needed)

## Sample Code Example
```python
# --- Welcome to variables! ---

# Step 1: Create variables
product_name = "Blue Shirt"
price = 999.99
quantity = 2
in_stock = True
discount = 0.15  # 15%

# Step 2: Use them
total_before_discount = price * quantity
discount_amount = total_before_discount * discount
total_after_discount = total_before_discount - discount_amount

# Step 3: Print results
print("Product:", product_name)
print("Price per item:", price)
print("Quantity:", quantity)
print("In stock?", in_stock)
print("Total before discount:", total_before_discount)
print("Discount amount:", discount_amount)
print("Final total:", total_after_discount)

# Step 4: Update variable
quantity = quantity + 1  # customer adds one more
print("Updated quantity:", quantity)

# Step 5: Input example (user enters data)
user_name = input("Enter your name: ")
print("Hello,", user_name)
```

Save as `variables.py` and run with `python variables.py`. Try changing values and see what happens.

## Methods (for Variables? – Important Note)
Variables themselves don't have methods—methods belong to the **data type** of the value stored in the variable.

Examples:
- If variable holds string: `name.upper()`
- If integer: `(age).bit_length()`
- If list: `cart.append("cap")`

So always check the type: `type(variable_name)` to see what methods are available.

## 10 Interview Questions (Beginner Level)
1. What is a variable in programming?
2. Give 5 rules for naming variables in Python.
3. What happens if you write `x = 10` and then `x = "hello"`?
4. Explain the difference between `=` and `==` in Python.
5. Why do we use descriptive names like `user_height` instead of `uh`?
6. What error do you get if you use a variable before assigning it?
7. How do you swap two variables in one line?
8. What is dynamic typing in Python? Give example.
9. Can variable names start with a number? Why or why not?
10. What does `del` do to a variable?

## 10 Coding Interview Questions (Beginner Level)
1. Create variables for name, age, height and print them in one sentence.
2. Write code to calculate and print area of rectangle (length × width).
3. Ask user for two numbers and print their sum, difference, product.
4. Create variables price and tax_rate, calculate final price with tax.
5. Swap values of two variables without using a third variable.
6. Convert temperature from Celsius to Fahrenheit (F = C × 9/5 + 32).
7. Calculate simple interest: principal × rate × time / 100.
8. Take user input for radius and calculate circle area (pi ≈ 3.14).
9. Create variables for hours and rate, calculate weekly pay.
10. Ask user for three numbers and print the largest one.

## Links for YouTube Reference Videos
1. "Python Variables for Absolute Beginners" by Corey Schafer  
   https://www.youtube.com/watch?v=khKv-8q7YmY (watch 0:00–8:00) – Clear, slow explanation with examples.

2. "Python Tutorial for Beginners – Variables" by Programming with Mosh  
   https://www.youtube.com/watch?v=_uQrJ0TkZlc&t=120s (first 10 minutes) – Great for zero-knowledge students.

3. "What are Variables in Python?" by freeCodeCamp  
   https://www.youtube.com/watch?v=eoO3Jf-h5uM (watch 5:00–15:00) – Visuals and simple analogies.

4. "Naming Variables in Python – Do's and Don'ts" by Telusko  
   https://www.youtube.com/watch?v=9f4rvaYcJHI&t=300s – Focus on naming rules and mistakes.

5. "Python Variables Explained with Examples" by Socratica  
   https://www.youtube.com/watch?v=PZRI1IfStY0 – 7min video, perfect for beginners with code-along.

**Tip for Novices**: Watch one video per day. Pause after each example, open your Python editor (VS Code or online Replit), type the code yourself, and change values to see what happens. Don't just watch—type along!

If you want the next file (e.g., `python_floats.md`, `python_strings.md`, or any other from the list), just say the name.