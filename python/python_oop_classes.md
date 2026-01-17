# python_oop_classes.md

## Definition of Class
A **class** in Python is a blueprint or template for creating objects.  
It defines what data (attributes) and behavior (methods) those objects will have.

For complete beginners with zero knowledge:  
Think of a class like a cookie cutter or a blueprint for a house:  
- The **class** is the design/cutter (shape, features)  
- The **object** (instance) is each actual cookie/house you make from it  
- You can make many cookies (objects) from one cutter (class), each slightly different if you want  

Example in your project:  
- Class `User` → blueprint for any user  
- Object `vikram_user = User("Vikram", 25)` → one specific user

## What and Why Classes (OOP – Object-Oriented Programming)
**What**: Classes let you create your own custom data types that bundle data + actions together.

**Why we need classes**:
- Organize code for real-world things (users, products, avatars, carts)
- Reuse code — define once, create many objects
- Group related data & functions (e.g., user has name + age + get_full_profile())
- Model relationships (inheritance – later file)
- Make code more readable & maintainable
- Support encapsulation (hide internal details)

In your project:
- `User` class — stores name, measurements, cart, premium status
- `Product` class — name, price, sizes, material
- `Avatar` class — height, measurements, methods to generate 3D mesh
- `Cart` class — items list, total calculation, checkout logic

Without classes, you'd use many separate variables/dictionaries — messy and hard to manage.

## Detailed Explanation How Classes Work in Python (for Absolute Beginners)

1. **Defining a Class**
   ```python
   class User:
       pass   # empty class (placeholder)
   ```

2. **Creating an Object (Instance)**
   ```python
   vikram = User()     # create object from class
   priya = User()      # another independent object
   ```

3. **The __init__ Method** (constructor – runs when object is created)
   ```python
   class User:
       def __init__(self, name, age):
           self.name = name      # attribute
           self.age = age
           self.is_premium = False  # default value

   # Create objects
   user1 = User("Vikram", 25)
   user2 = User("Priya", 22)

   print(user1.name)       # Vikram
   print(user2.age)        # 22
   ```

   - `self` is mandatory — refers to the current object
   - `self.name = ...` creates an attribute (like a variable attached to the object)

4. **Instance Methods** (functions inside class)
   ```python
   class User:
       def __init__(self, name, age):
           self.name = name
           self.age = age
           self.cart = []

       def add_to_cart(self, product):
           self.cart.append(product)
           print(f"{self.name} added {product} to cart")

       def get_cart_count(self):
           return len(self.cart)

   vikram = User("Vikram", 25)
   vikram.add_to_cart("Blue Shirt")
   vikram.add_to_cart("Cap")
   print(vikram.get_cart_count())  # 2
   ```

   - Methods always have `self` as first parameter
   - Call with `object.method()` — `self` is automatically passed

5. **Class Attributes** (shared by all objects)
   ```python
   class User:
       user_count = 0   # class attribute

       def __init__(self, name):
           self.name = name
           User.user_count += 1   # increment shared counter

   u1 = User("Vikram")
   u2 = User("Priya")
   print(User.user_count)   # 2 (same for all)
   ```

6. **self vs Class Name**
   - `self.attribute` → per-object (instance attribute)
   - `ClassName.attribute` → shared by all objects (class attribute)

7. **Common Pitfalls for Novices**
   - Forgetting `self` in method parameters → TypeError
   - Forgetting `self.` when using attribute → NameError
   - Indentation errors (class methods must be indented)
   - Creating object without required arguments in `__init__`
   - Confusing class vs instance attributes

8. **Special Methods** (dunder/magic methods – intro)
   - `__init__` : constructor
   - `__str__` : how object prints when using `print(obj)`
   ```python
   def __str__(self):
       return f"User: {self.name}, Age: {self.age}"
   ```

## Syntax
```python
class ClassName:
    # class attribute (shared)
    shared_value = 0

    def __init__(self, param1, param2):
        # instance attributes (per object)
        self.param1 = param1
        self.param2 = param2

    def method_name(self):
        # use self to access attributes
        return self.param1 + self.param2

# Create object
obj = ClassName(value1, value2)

# Use
print(obj.method_name())
```

## Sample Code Example (Practical for your project)
```python
# --- Mini User & Product classes for your wearables app ---

class User:
    def __init__(self, name, age, height_cm):
        self.name = name
        self.age = age
        self.height_cm = height_cm
        self.measurements = {}      # will store chest, waist, etc.
        self.cart = []
        self.is_premium = False

    def add_measurement(self, key, value):
        self.measurements[key] = value
        print(f"Added {key}: {value} cm for {self.name}")

    def add_to_cart(self, product_name):
        self.cart.append(product_name)
        print(f"{self.name} added {product_name} to cart")

    def get_cart_summary(self):
        if not self.cart:
            return "Cart is empty"
        return f"{self.name}'s cart: {', '.join(self.cart)}"

class Product:
    def __init__(self, name, price, sizes):
        self.name = name
        self.price = price
        self.sizes = sizes

    def __str__(self):
        return f"{self.name} - ₹{self.price} | Sizes: {self.sizes}"

# Usage
vikram = User("Vikram", 25, 175.5)
vikram.add_measurement("chest", 90)
vikram.add_measurement("waist", 80)

vikram.add_to_cart("Blue Shirt")
vikram.add_to_cart("Black Cap")

print(vikram.get_cart_summary())

shirt = Product("Blue Shirt", 999.99, [38, 40, 42])
print(shirt)  # Uses __str__
```

Run this — create objects, add data, see how organized and reusable it is.

## 10 Interview Questions (Beginner Level)
1. What is a class in Python?
2. What is the difference between class and object?
3. What is the purpose of `__init__` method?
4. What does `self` mean in a class method?
5. Explain instance attribute vs class attribute.
6. How do you create an object from a class?
7. What is a method in a class?
8. Why do we use classes instead of just dictionaries?
9. What is the `__str__` method used for?
10. Give a real-world example of when to use a class.

## 10 Coding Interview Questions (Beginner Level)
1. Create a simple `Car` class with attributes color and speed.
2. Add a method `accelerate()` that increases speed by 10.
3. Create `Student` class with name, marks, and method to get grade (A/B/C).
4. Make `Rectangle` class with length, width, and method to calculate area.
5. Create `Product` class with name, price, and method to apply discount.
6. Add class attribute `total_products` that counts how many products created.
7. Write `__str__` method for `User` class to print nice summary.
8. Create `BankAccount` class with balance, deposit(), withdraw() methods.
9. Make `Cart` class that can add/remove items and calculate total.
10. Create `Avatar` class with height, measurements dict, and method to print summary.

## Links for YouTube Reference Videos
1. "Python OOP Tutorial 1 – Classes and Instances" – Corey Schafer  
   https://www.youtube.com/watch?v=ZDa-Z5JzLYM (first video in series, 20min) – Best beginner series, very clear.

2. "Object Oriented Programming in Python" – Programming with Mosh  
   https://www.youtube.com/watch?v=JeznW_7DlB0 (first 20 minutes) – Simple & practical.

3. "Python Classes & Objects Explained" – freeCodeCamp  
   https://www.youtube.com/watch?v=Ej_02ICOIgs (watch class section) – Visual and easy.

4. "Understanding Classes in Python" – Telusko  
   https://www.youtube.com/watch?v=ZDa-Z5JzLYM – 15min live coding.

5. "Python OOP – __init__ and self" – Socratica  
   https://www.youtube.com/watch?v=apACNr7DC_s – 10min, great analogies.

**Tip for Novices**  
Classes feel abstract at first — think of them as "custom types".  
Practice:  
1. Write `class Person: pass`  
2. Add `__init__(self, name): self.name = name`  
3. Create `p = Person("Vikram")`  
4. Print `p.name`  
5. Add method `def say_hi(self): print("Hi, I'm", self.name)`  
6. Call `p.say_hi()`

Do this slowly — soon you'll see how powerful it is for modeling users, products, avatars in your app.

Next file? Say: "next: python_oop_inheritance.md" or any other (python_oop_polymorphism.md, python_oop_encapsulation.md, etc.)