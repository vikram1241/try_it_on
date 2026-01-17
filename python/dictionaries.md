# python_dictionaries.md

## Definition of Dictionary
A **dictionary** in Python (often called **dict**) is an unordered, mutable collection of key-value pairs.  
Each **key** is unique and maps to a **value**. It is defined using curly braces `{}` with `key: value` format.

For complete beginners with zero knowledge:  
Think of a dictionary like a real-life phone book or contact list on your phone:  
- The **key** is the name (e.g., "Vikram")  
- The **value** is the phone number or info (e.g., "9876543210")  
- You look up by name (key) to get the number (value) very quickly  
- You can add, change, or delete entries anytime  

In Python, dictionaries are also called **hash maps** or **associative arrays** in other languages.

Examples from your project:
- `user_profile = {"name": "Vikram", "height": 175.5, "is_premium": True}`
- `product = {"name": "Blue Shirt", "price": 999.99, "sizes": [38, 40, 42]}`
- `cart = {"shirt_001": 2, "cap_005": 1}` — item ID → quantity

## What and Why Dictionaries
**What**: Dictionaries store data as pairs: a unique key → associated value.

**Why we need dictionaries**:
- Fast lookup by key (O(1) average time — very fast)
- Organize related data (like a record or row in a table)
- Handle key-value data naturally (JSON, user settings, product attributes)
- Keys can be strings, numbers, tuples (immutable), values can be anything (lists, other dicts, etc.)

In your project:
- Store user measurements: `{"height": 175, "chest": 90, "waist": 80}`
- Product catalog: `{"p001": {"name": "Shirt", "price": 999}}`
- Cart: item code → quantity
- Settings: `{"theme": "dark", "show_booklet": True}`
- Without dictionaries, you'd need many separate variables or hard-to-search lists

Dictionaries make your code clean, readable, and fast for lookups.

## Detailed Explanation How Dictionaries Work in Python (for Absolute Beginners)
Step-by-step:

1. **Creation**  
   ```python
   empty_dict = {}
   user = {"name": "Vikram", "age": 25}
   product = dict(name="Shirt", price=999.99)  # alternative way
   ```

2. **Keys must be unique & immutable**  
   - Valid keys: strings, numbers, tuples (immutable)
   - Invalid keys: lists, sets, other dicts (mutable)
   ```python
   d = {1: "one", "two": 2, (3,4): "point"}  # OK
   d[[5,6]] = "list"  # ERROR! unhashable type: 'list'
   ```

3. **Access & Modify**  
   ```python
   print(user["name"])         # "Vikram"
   user["age"] = 26            # change value
   user["city"] = "Airoli"     # add new key-value
   del user["age"]             # remove key
   ```

4. **Get with default (safe access)**  
   ```python
   print(user.get("phone", "Not found"))  # "Not found" if missing
   ```

5. **Check existence**  
   ```python
   "name" in user          # True
   "phone" in user         # False
   ```

6. **Looping**  
   ```python
   for key in user:
       print(key, user[key])

   for k, v in user.items():
       print(f"{k}: {v}")
   ```

7. **Nested Dictionaries** (very useful)
   ```python
   order = {
       "user": {"name": "Vikram", "city": "Airoli"},
       "items": {"shirt_001": 2, "cap_005": 1},
       "total": 2999.98
   }
   print(order["user"]["city"])  # "Airoli"
   ```

8. **Dictionary Comprehension** (short creation)
   ```python
   squares = {x: x**2 for x in range(5)}  # {0:0, 1:1, 2:4, 3:9, 4:16}
   ```

9. **Common Pitfalls for Novices**
   - Using mutable key: `d[[1,2]] = 3` → TypeError
   - KeyError: `print(d["missing"])` → crash (use `.get()`)
   - Forgetting quotes on string keys: `d[name] = "Vikram"` → NameError
   - Modifying while looping: can cause RuntimeError (make copy)

10. **Memory & Performance**  
    - Fast lookups (hash table internally)
    - Order preserved since Python 3.7 (insertion order)

## Syntax
```python
# Creation
profile = {"name": "Vikram", "age": 25, "premium": True}

# Access
print(profile["name"])

# Add / Update
profile["city"] = "Airoli"
profile["age"] = 26

# Remove
del profile["premium"]

# Safe get
phone = profile.get("phone", "Not set")
```

## Sample Code Example (Practical for your project)
```python
# --- Mini user profile & cart for your app ---

# Step 1: Create user profile dictionary
user_profile = {
    "name": "Vikram",
    "age": 25,
    "height_cm": 175.5,
    "measurements": {"chest": 90, "waist": 80, "inseam": 32},
    "is_premium": False,
    "preferred_size": "M"
}

# Step 2: Access and print
print("User:", user_profile["name"])
print("Height:", user_profile["height_cm"], "cm")
print("Chest measurement:", user_profile["measurements"]["chest"])

# Step 3: Update & add
user_profile["age"] = 26
user_profile["city"] = "Airoli"
user_profile["is_premium"] = True

# Step 4: Cart as dictionary (item code → quantity)
cart = {
    "shirt_001": 2,
    "cap_005": 1,
    "watch_007": 1
}

# Step 5: Calculate total items
total_items = sum(cart.values())
print("Items in cart:", total_items)

# Step 6: Check if item exists
if "shirt_001" in cart:
    print("Shirt quantity:", cart["shirt_001"])

# Step 7: Loop through cart
print("\nCart contents:")
for item, qty in cart.items():
    print(f"- {item}: {qty} pcs")
```

Run this — change keys/values, add new items, see how flexible dictionaries are.

## Methods (most useful – with one-line definition + example)
- `get(key, default=None)`: Returns value for key or default if missing. Example: `d.get("age", 0)` → 0 if no age
- `keys()`: Returns view of all keys. Example: `list(d.keys())` → ['name', 'age']
- `values()`: Returns view of all values. Example: `list(d.values())`
- `items()`: Returns view of (key, value) tuples. Example: `for k,v in d.items():`
- `update(other_dict)`: Adds/updates from another dict. Example: `d.update({"city": "Mumbai"})`
- `pop(key, default)`: Removes key and returns value (or default). Example: `age = d.pop("age", None)`
- `popitem()`: Removes and returns last (key, value) pair. Example: `item = d.popitem()`
- `clear()`: Removes all items. Example: `d.clear()`
- `copy()`: Shallow copy. Example: `new_d = d.copy()`
- `setdefault(key, default)`: Returns value if key exists, else sets & returns default. Example: `qty = cart.setdefault("new_item", 0)`

## 10 Interview Questions (Beginner Level)
1. What is a dictionary in Python?
2. How is dictionary different from list?
3. Can dictionary keys be lists? Why or why not?
4. What happens if you use the same key twice when creating a dict?
5. How do you access a value safely without KeyError?
6. What does `.items()` return?
7. Explain `get()` method with example.
8. Why are dictionaries faster for lookups than lists?
9. What is dictionary unpacking?
10. How do you merge two dictionaries?

## 10 Coding Interview Questions (Beginner Level)
1. Create a dictionary for a user with name, age, city and print all keys.
2. Add a new key "phone" to the dictionary.
3. Update age to current age + 1.
4. Check if "email" key exists, if not set to "not provided".
5. Print all values in the dictionary.
6. Remove "city" key and print the dict.
7. Loop through dictionary and print "Key: value" for each.
8. Create a dictionary from two lists: names = ["A", "B"], ages = [25, 30].
9. Count frequency of words in a sentence using dictionary.
10. Merge two dictionaries (user info + preferences).

## Links for YouTube Reference Videos
1. "Python Dictionaries for Beginners" – Corey Schafer  
   https://www.youtube.com/watch?v=daefaLgNdn0 (full 18min) – Best beginner video, very thorough.

2. "Python Dictionary Tutorial" – Programming with Mosh  
   https://www.youtube.com/watch?v=9f4rvaYcJHI&t=1800s (dict section ~30:00–45:00) – Clear with examples.

3. "Everything About Dictionaries in Python" – freeCodeCamp  
   https://www.youtube.com/watch?v=W8KRzm-HUcc&t=2400s (watch dict part) – Many real examples.

4. "Python Dictionaries – Methods & Use Cases" – Telusko  
   https://www.youtube.com/watch?v=uoS7Yg3l3hA – 12min, live coding all important methods.

5. "Understanding Python Dictionaries" – Socratica  
   https://www.youtube.com/watch?v=PZRI1IfStY0 – 10min, great analogies for keys/values.

**Tip for Novices**  
Dictionaries are like mini-databases in code.  
Practice:  
1. Create `user = {}`  
2. `user["name"] = "Vikram"`  
3. `user["height"] = 175`  
4. Print `user`  
5. Add more keys, change values, delete one  
6. Try `user["missing"]` → see KeyError, then use `.get()`  

This will make you very comfortable for storing user measurements and product data in your app.

Next file? Say: "next: python_sets.md" or any other (python_conditionals.md, python_functions.md, python_loops.md, etc.)