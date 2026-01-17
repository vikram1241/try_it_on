# python_modules_packages.md

## Definition of Module and Package
A **module** in Python is a single `.py` file that contains Python code (functions, classes, variables, etc.).  
A **package** is a collection of modules organized in a folder with a special `__init__.py` file (even if empty).

For complete beginners with zero knowledge:  
Think of a module like a single recipe book (one `.py` file with related recipes/functions).  
A package is like a whole cookbook shelf — a folder containing many recipe books (modules) + a table of contents (`__init__.py`) so Python knows it's a package.

Examples from your project:
- `user_utils.py` module — functions for user profile handling
- `ai_tryon` package — folder with modules like `avatar.py`, `draping.py`, `gen_ai.py`

## What and Why Modules & Packages
**What**:
- **Module**: One `.py` file you can import and reuse code from
- **Package**: Folder of modules with `__init__.py` — lets you organize large projects

**Why we need them**:
- **Reuse code** — write once, use in many places/files
- **Organize big projects** — your app will have hundreds of lines; one file becomes unmanageable
- **Avoid name conflicts** — separate code into logical groups
- **Share code** — others can use your module/package
- **Clean structure** — separate concerns (e.g., one module for database, one for AI, one for UI)
- **Standard library** — Python comes with many built-in modules (math, random, json, datetime, os)

In your project:
- `utils.py` — helper functions (calculate total, format price)
- `ai/` package — `avatar_gen.py`, `tryon_viton.py`, `fabric_texture.py`
- `ecommerce/` package — `cart.py`, `payment.py`, `booklet.py`
- Import built-in: `import json` for saving user data

Without modules/packages, your entire app would be in one giant file — impossible to manage.

## Detailed Explanation How Modules & Packages Work in Python (for Absolute Beginners)

### 1. Creating & Using a Simple Module
Create file `math_utils.py`:
```python
# math_utils.py
def add(a, b):
    return a + b

def multiply(a, b):
    return a * b

PI = 3.14159
```

Use it in another file `main.py`:
```python
# main.py
import math_utils

result = math_utils.add(5, 3)
print(result)               # 8

print(math_utils.PI)        # 3.14159
```

### 2. Import Styles
- `import module_name` → use `module_name.function()`
- `from module_name import function` → use `function()` directly
- `from module_name import *` → import everything (avoid — pollutes namespace)
- `import module_name as alias` → shorter name

Examples:
```python
from math_utils import add, multiply
print(add(2, 3))            # 5

import math_utils as mu
print(mu.multiply(4, 5))    # 20
```

### 3. Creating a Package
Folder structure:
```
my_project/
├── main.py
└── utils/                  # this is the package
    ├── __init__.py         # can be empty
    ├── math.py
    └── user.py
```

`utils/math.py`:
```python
def square(n):
    return n * n
```

`main.py`:
```python
from utils.math import square

print(square(5))            # 25
```

`__init__.py` makes folder a package — Python knows to look inside for modules.

### 4. Built-in Modules (no install needed)
```python
import math
print(math.sqrt(16))        # 4.0

import random
print(random.randint(1, 10)) # random number 1-10

import datetime
today = datetime.date.today()
print(today)                # 2026-01-17 (example)

import os
print(os.getcwd())          # current working directory
```

### 5. Installing External Packages (using pip – later topic)
```bash
pip install requests
```
Then:
```python
import requests
response = requests.get("https://api.example.com")
```

### 6. `__name__ == "__main__"` (very useful)
```python
# in my_module.py
def useful_function():
    print("Doing useful work")

if __name__ == "__main__":
    print("This runs only if file is run directly, not when imported")
    useful_function()
```

- When you run `python my_module.py` → code in if block runs
- When you `import my_module` → if block skipped

Keeps test code separate from reusable code.

### 7. Common Pitfalls for Novices
- Circular imports: file A imports B, B imports A → crash
- Wrong import path: `from utils import math` (if utils is package)
- Forgetting `__init__.py` in package folder (pre-Python 3.3, required)
- Naming module same as built-in: `import random` but you have `random.py` → shadows built-in
- Relative imports in scripts: `from .utils import ...` (needs package structure)

## Syntax
```python
# Import whole module
import math_utils

# Import specific items
from math_utils import add, PI

# Import with alias
import math_utils as mu

# Package import
from utils.math import square

# Run only if direct execution
if __name__ == "__main__":
    # test code here
```

## Sample Code Example (Practical for your project)
Folder structure:
```
wearables_app/
├── main.py
└── helpers/
    ├── __init__.py
    ├── cart.py
    └── user.py
```

`helpers/cart.py`:
```python
# helpers/cart.py
def calculate_total(items):
    prices = [item["price"] for item in items]
    return sum(prices)

def add_to_cart(cart, product):
    cart.append(product)
    print(f"Added {product['name']} to cart")
```

`helpers/user.py`:
```python
# helpers/user.py
def create_profile(name, height):
    return {"name": name, "height_cm": height}
```

`main.py`:
```python
# main.py
from helpers.cart import calculate_total, add_to_cart
from helpers.user import create_profile

# Create user
user = create_profile("Vikram", 175.5)

# Shopping cart
cart = []
add_to_cart(cart, {"name": "Blue Shirt", "price": 999.99})
add_to_cart(cart, {"name": "Cap", "price": 499.50})

# Calculate & show
total = calculate_total(cart)
print(f"Total for {user['name']}: ₹{total}")
```

Run `python main.py` — see modular code in action.

## 10 Interview Questions (Beginner Level)
1. What is the difference between a module and a package?
2. How do you create an empty package?
3. What is the purpose of `__init__.py`?
4. Explain `if __name__ == "__main__":` and why it's useful.
5. What are `*args` and `**kwargs` in function imports?
6. How do you import a specific function from a module?
7. What is the difference between `import module` and `from module import *`?
8. How do you use an alias when importing?
9. Why can't you import from a folder without `__init__.py` (in older Python)?
10. Give an example of when to use a package in a real project.

## 10 Coding Interview Questions (Beginner Level)
1. Create a module `math_utils.py` with add() and multiply() functions. Import and use in main file.
2. Make a package `utils` with module `cart.py` containing calculate_total().
3. Write a module that has a function to greet user — run it only when file is executed directly.
4. Create `config.py` module with constants (PI, TAX_RATE) and import them.
5. Write function in module to save user name to file — import and call.
6. Make package `ai` with module `tryon.py` having placeholder function generate_avatar().
7. Use random module to pick random product from list.
8. Import datetime and print current date in main file.
9. Create module `validators.py` with is_valid_size(size) function.
10. Organize your project: create helpers package with cart and user modules.

## Links for YouTube Reference Videos
1. "Python Modules and Packages Explained" – Corey Schafer  
   https://www.youtube.com/watch?v=CqvZ3vGoGs0 (full 30min) – Best in-depth beginner video.

2. "Modules & Packages in Python" – Programming with Mosh  
   https://www.youtube.com/watch?v=9f4rvaYcJHI&t=3600s (module section ~1:00:00–1:15:00) – Clear & practical.

3. "Understanding __name__ == '__main__'" – freeCodeCamp  
   https://www.youtube.com/watch?v=PWdPLZvdO_I (watch modules section) – Explains why it's used.

4. "Python Packages & __init__.py" – Telusko  
   https://www.youtube.com/watch?v=uoS7Yg3l3hA – 10min, shows folder structure live.

5. "Modules vs Packages in Python" – Socratica  
   https://www.youtube.com/watch?v=PZRI1IfStY0 – 8min, great for beginners.

**Tip for Novices**  
Modules/packages make your project grow without chaos.  
Practice:  
1. Create file `utils.py` with `def say_hi(name): print("Hi", name)`  
2. In another file `main.py`: `from utils import say_hi; say_hi("Vikram")`  
3. Make folder `helpers`, add `__init__.py` (empty file), move utils.py inside  
4. Import: `from helpers.utils import say_hi`  
5. Add more functions — see how organized it becomes

This structure is how professional apps are built — your try-on + e-commerce will use many modules/packages.

Next file? Say: "next: python_oop_classes.md" or any other (python_oop_inheritance.md, opencv_image_basics.md, flask_setup_routes.md, etc.)