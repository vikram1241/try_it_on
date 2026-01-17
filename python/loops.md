# python_loops.md

## Definition of Loops
**Loops** in Python are used to execute a block of code repeatedly — either a fixed number of times or until a condition becomes false.  
There are two main types: `for` loops and `while` loops.

For complete beginners with zero knowledge:  
Imagine you need to say "Hello" to 10 friends.  
Without loops: write `print("Hello")` 10 times — boring and error-prone.  
With loops: write the code once and tell Python "do this 10 times" — easy and clean.

Loops are essential in your project:  
- Show every product in the catalog  
- Loop through user's cart items to calculate total  
- Process multiple photos for 360-degree avatar  
- Keep asking user for valid input until correct

## What and Why Loops
**What**: Loops repeat code automatically.

**Why we need loops**:
- Avoid writing the same code many times (DRY principle)
- Handle collections (lists, strings, ranges) easily
- Process data (sum prices, check sizes)
- Wait for conditions (keep trying until user enters correct size)
- Make programs scalable (works for 1 or 1000 items)

Without loops, your app couldn't handle more than a few items or users.

## Detailed Explanation How Loops Work in Python (for Absolute Beginners)
Step-by-step:

### 1. for Loop (most common for beginners)
Repeats for each item in a sequence (list, tuple, string, range, etc.)
```python
fruits = ["apple", "banana", "cherry"]

for fruit in fruits:
    print("I like", fruit)
```
Output:
```
I like apple
I like banana
I like cherry
```

- `for` keyword  
- Variable (`fruit`) takes each value one by one  
- `in` keyword  
- Sequence (list, range, etc.)  
- Colon `:`  
- Indented block runs for each item

### 2. range() — Create Number Sequences
```python
for i in range(5):           # 0,1,2,3,4
    print(i)

for i in range(1, 6):        # 1 to 5
    print(i)

for i in range(1, 10, 2):    # 1,3,5,7,9 (step 2)
    print(i)
```

### 3. while Loop
Repeats as long as condition is True
```python
count = 1

while count <= 5:
    print("Count:", count)
    count += 1   # MUST update! Otherwise infinite loop
```

### 4. Loop Control Statements
- `break`: Exit loop immediately
- `continue`: Skip current iteration, go to next
- `pass`: Do nothing (placeholder)
```python
for i in range(10):
    if i == 5:
        break          # stop at 5
    if i % 2 == 0:
        continue       # skip even numbers
    print(i)           # prints 1,3,5,7,9
```

### 5. Nested Loops (loop inside loop)
```python
for i in range(1, 4):
    for j in range(1, 4):
        print(f"{i} × {j} = {i*j}")
```

### 6. for-else & while-else (runs if no break occurred)
```python
for i in range(5):
    if i == 10:
        break
else:
    print("Loop completed normally")  # this runs
```

### 7. enumerate() — Get Index + Value
```python
products = ["shirt", "cap", "watch"]
for index, product in enumerate(products, start=1):
    print(f"{index}. {product}")
```

### 8. Common Pitfalls for Novices
- Infinite loop: `while True:` without break → program hangs
- Forgetting to update counter in while loop
- Wrong indentation → code runs too few/many times
- Modifying list while looping → skips items
- Using `==` instead of `=` in conditions

## Syntax
```python
# for loop
for variable in sequence:
    # code to repeat

# while loop
while condition:
    # code to repeat
    # MUST update condition!

# break & continue
if something:
    break
if something_else:
    continue
```

## Sample Code Example (Practical for your project)
```python
# --- Mini cart & size checker for your wearables app ---

# Step 1: Cart as list
cart = ["Blue Shirt", "Black Cap", "Leather Watch"]

# Step 2: for loop - show cart with numbers
print("Your Cart:")
for i, item in enumerate(cart, start=1):
    print(f"{i}. {item}")

# Step 3: while loop - ask for valid size
available_sizes = [38, 40, 42, 44]
user_size = 0

while user_size not in available_sizes:
    try:
        user_size = int(input("Enter size (38-44): "))
        if user_size not in available_sizes:
            print("Sorry, size not available. Try again.")
    except ValueError:
        print("Please enter a number!")

print("Size", user_size, "confirmed!")

# Step 4: Nested loop - show all combinations
colors = ["Navy", "Black"]
for color in colors:
    for size in available_sizes:
        print(f"{color} Shirt - Size {size}")

# Step 5: break example - stop if out of stock
in_stock = True
for item in cart:
    if not in_stock:
        print("Stopping – out of stock!")
        break
    print("Processing:", item)
```

Run this — add items, change sizes, see loops in action.

## 10 Interview Questions (Beginner Level)
1. What is the difference between `for` and `while` loops?
2. How do you stop a loop early?
3. What happens if you forget to update the counter in a while loop?
4. Explain `range(1, 10, 2)` with output.
5. What does `enumerate()` do? Why is it useful?
6. What is an infinite loop? How to avoid it?
7. Can you have a loop inside another loop? Give example.
8. What is the purpose of `continue` statement?
9. Explain `for-else` construct.
10. How do you loop through a dictionary's keys and values?

## 10 Coding Interview Questions (Beginner Level)
1. Print numbers 1 to 10 using for and while loops.
2. Print even numbers from 1 to 20.
3. Ask user for numbers until they enter 0, then print sum.
4. Print multiplication table of 5 (5 × 1 = 5 ... 5 × 10 = 50).
5. Loop through list of products and print only those starting with "B".
6. Use break to stop loop when item == "watch" is found.
7. Use continue to skip odd numbers in 1–10.
8. Nested loop: print all pairs of colors and sizes.
9. Sum all items in a list using loop.
10. Count how many times "shirt" appears in cart list.

## Links for YouTube Reference Videos
1. "Python Loops for Beginners – for & while" – Corey Schafer  
   https://www.youtube.com/watch?v=6iF8Xb7Z3wQ (full 20min) – Excellent, clear, slow-paced.

2. "For Loops & While Loops in Python" – Programming with Mosh  
   https://www.youtube.com/watch?v=6iF8Xb7Z3wQ&t=1200s (first 15 minutes) – Very beginner-friendly.

3. "Python Loops Tutorial" – freeCodeCamp  
   https://www.youtube.com/watch?v=PWdPLZvdO_I (watch loops section) – Visual and practical.

4. "Understanding for & while Loops" – Telusko  
   https://www.youtube.com/watch?v=uoS7Yg3l3hA – 12min live coding examples.

5. "Python Loops – break, continue, pass" – Socratica  
   https://www.youtube.com/watch?v=PZRI1IfStY0 – 8min, explains control statements well.

**Tip for Novices**  
Loops are where repetition becomes easy.  
Practice:  
1. Write `for i in range(5): print("Hello")`  
2. Change range to 1,11  
3. Add `if i == 3: break`  
4. Try while loop: `count = 0; while count < 5: print(count); count += 1`  

This is how you'll loop through cart items, sizes, or product photos in your app.

Next file? Say: "next: python_oop_classes.md" or any other (python_oop_inheritance.md, python_oop_polymorphism.md, python_oop_encapsulation.md, etc.)