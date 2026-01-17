# python_datatypes.md

## Definition of Data Types
A **data type** in Python tells the computer what kind of value a variable holds and what operations you can perform on it. Every piece of data in Python belongs to a specific type.

For absolute beginners with zero knowledge:  
Think of data types like different kinds of containers in your kitchen:  
- A small bowl for sugar (integer – whole numbers)  
- A measuring cup for water (float – numbers with decimals)  
- A label on a jar saying "sugar" (string – text)  
- A light switch that is either ON or OFF (boolean – true/false)  

Python automatically figures out the type when you assign a value — you don't have to tell it in advance (this is called **dynamic typing**).

## What and Why Data Types
**What**: Data types define the kind of information stored in variables: numbers, text, true/false values, collections of items, etc.

**Why we need them**:
- The computer needs to know how much memory to use (integer takes less than a very long text)
- What operations are allowed (you can add numbers, but not add text to a number)
- How to display and compare values
- Avoid mistakes (adding "5" + "10" as text gives "510" instead of 15)

In your project:
- **integers/floats**: body measurements (height 175 cm, waist 80.5 cm)
- **strings**: product names ("Blue Cotton Shirt"), user names
- **booleans**: is_in_stock = True, has_discount = False
- **lists/dicts**: cart items, user measurements dictionary

## Detailed Explanation How Data Types Work in Python (Beginner-Friendly)
1. **Dynamic Typing**  
   Python decides the type automatically.  
   ```python
   x = 5          # x is int
   x = 5.5        # now x is float
   x = "hello"    # now x is str
   ```
   This makes coding faster for beginners but you must be careful not to mix types accidentally.

2. **Mutable vs Immutable**  
   - **Immutable** (cannot be changed after creation): int, float, str, tuple, bool  
     If you do `x = x + 1`, Python creates a **new** object and points x to it.  
   - **Mutable** (can be changed in place): list, dict, set  
     `lst = [1,2]; lst.append(3)` changes the same list object.

3. **Primitive vs Non-Primitive (Important for Novices)**  
   In languages like Java or C, there are **primitive types** (basic, not objects, fixed size, stored directly in memory): int, float, boolean, char.  
   In Python, **there are no primitives** — everything is an object (non-primitive).  
   - Even `5` is an object of class `int`  
   - Even `True` is an object of class `bool`  
   - This means they have methods: `5.bit_length()`, `"hello".upper()`  
   - Advantage: uniform behavior, easy to extend  
   - Disadvantage: slightly more memory and slower than true primitives (but for most apps, you don't notice)

4. **Common Built-in Data Types** (the main ones you'll use)
   - `int`       – whole numbers (arbitrary size)
   - `float`     – decimal numbers
   - `bool`      – True or False
   - `str`       – text (strings)
   - `list`      – ordered, changeable collection
   - `tuple`     – ordered, unchangeable collection
   - `dict`      – key-value pairs (like a real dictionary)
   - `set`       – unordered, unique items

5. **Type Checking & Conversion**
   - Check type: `type(5)` → `<class 'int'>`
   - Convert: `int(3.9)` → 3, `float("3.14")` → 3.14, `str(42)` → "42"
   - Invalid conversion → ValueError (handle with try/except)

6. **Memory & Performance Tips for Novices**
   - Small integers (-5 to 256) are cached → same object reused
   - Strings with same content may be interned (shared) if short
   - Don't worry about memory yet — Python handles it automatically

## Syntax & Examples (All Major Types)
```python
# Integer
age = 25
big_number = 10**100  # no problem

# Float
price = 999.99
scientific = 1.23e-4  # 0.000123

# Boolean
is_adult = True
has_discount = False

# String
name = "Vikram"
product = 'Blue Shirt'

# List (mutable, ordered)
cart = ["shirt", "cap", "watch"]
cart.append("shoes")

# Tuple (immutable, ordered)
sizes = (32, 34, 36)  # can't change

# Dictionary (key-value)
user = {
    "name": "Vikram",
    "height": 175.5,
    "in_stock": True
}

# Set (unique, unordered)
colors = {"red", "blue", "red"}  # becomes {"red", "blue"}
```

## Sample Code Example (Putting It All Together)
```python
# --- Mini shopping example ---

# Variables with different types
product_name = "Red Cotton Shirt"      # str
price = 799.50                         # float
quantity = 3                           # int
in_stock = True                        # bool
sizes_available = [38, 40, 42]         # list
measurements = {"chest": 90, "waist": 80}  # dict

# Calculations
total = price * quantity
tax = total * 0.18
final_price = total + tax

# Print everything nicely
print("Product:", product_name)
print("Price per item:", price)
print("Quantity:", quantity)
print("In stock?", in_stock)
print("Total before tax:", total)
print("Tax (18%):", tax)
print("Final price:", final_price)
print("Available sizes:", sizes_available)
print("User measurements:", measurements)
```

Run this code — see how different types work together.

## Checking Types & Conversion
```python
print(type(42))          # <class 'int'>
print(type(3.14))        # <class 'float'>
print(type("hello"))     # <class 'str'>
print(type(True))        # <class 'bool'>
print(type([1,2,3]))     # <class 'list'>

# Conversion examples
num_str = "100"
num = int(num_str)       # 100
float_num = float("3.14")# 3.14
text = str(500)          # "500"
```

## 10 Interview Questions (Beginner Level)
1. What is a data type in Python?
2. Name the main built-in data types.
3. What is dynamic typing? Give an example.
4. What is the difference between mutable and immutable types?
5. Is `int` primitive or non-primitive in Python? Explain.
6. What does `type()` function do?
7. What happens when you convert float to int?
8. Why do we need different data types?
9. Give an example of when to use list vs tuple.
10. What is a dictionary used for?

## 10 Coding Interview Questions (Beginner Level)
1. Create variables of each main type (int, float, str, bool, list, dict) and print their types.
2. Take user input for name and age, print "Hello [name], you are [age] years old."
3. Calculate and print area of rectangle using length and width (float).
4. Create a list of 5 products and print the second one.
5. Make a dictionary for a user with name, age, city, and print it.
6. Convert string "123.45" to float and add 10 to it.
7. Check if a number is positive, negative, or zero (use bool).
8. Create a tuple of 4 colors and try to change one (see the error).
9. Make a set from list [1,2,2,3,3] and print it.
10. Print "Welcome" 5 times using a loop (later topic) and a variable count.

## Links for YouTube Reference Videos
1. "Python Data Types Explained for Beginners" – Corey Schafer  
   https://www.youtube.com/watch?v=khKv-8q7YmY (watch 0:00–12:00) – Clear & slow, perfect start.

2. "Python Data Types Tutorial" – Programming with Mosh  
   https://www.youtube.com/watch?v=_uQrJ0TkZlc&t=300s (first 15 minutes) – Very beginner-friendly with visuals.

3. "Python Data Types – int, float, str, bool, list, dict" – freeCodeCamp  
   https://www.youtube.com/watch?v=eoO3Jf-h5uM (watch 10:00–25:00) – Code along section.

4. "Understanding Mutable vs Immutable in Python" – Telusko  
   https://www.youtube.com/watch?v=9f4rvaYcJHI – 10min explanation with examples.

5. "Python for Absolute Beginners – Data Types" – Socratica  
   https://www.youtube.com/watch?v=PZRI1IfStY0 – Short, clear, great analogies.

**Advice for Novices**:  
Watch videos with a notebook and Python open. After each video, type every example yourself — change numbers, names, and see what happens. Don't copy-paste only — typing helps you learn faster.

Ready for next file? Say: "next: python_floats.md" or any other name from the list.