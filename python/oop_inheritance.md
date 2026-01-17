# python_oop_inheritance.md

## Definition of Inheritance
**Inheritance** in Python is a core concept of Object-Oriented Programming (OOP) that allows one class (called **child** or **subclass**) to inherit attributes and methods from another class (called **parent** or **superclass**).  
The child class can reuse, extend, or override (change) the parent's behavior.

For complete beginners with zero knowledge:  
Think of inheritance like family traits:  
- A **parent** (base class) has certain features (eye color, height, skills)  
- A **child** (derived class) automatically gets most of those features  
- The child can also have extra features (new skills) or change some (different eye color)  

In code, instead of rewriting the same code in every class, you inherit from a parent and only add/change what's different.

Example in your project:  
- Base class `Product` — common things all products have (name, price, description)  
- Child class `Shirt` — inherits from Product + adds shirt-specific things (sizes, collar type)  
- Child class `Watch` — inherits from Product + adds watch-specific things (strap material, water resistance)

This saves code and keeps things organized.

## What and Why Inheritance
**What**: Inheritance lets a new class "borrow" code from an existing class.

**Why we need inheritance**:
- **Code reuse** — don't repeat common code (DRY principle)
- **Organize hierarchy** — model real-world "is-a" relationships (Shirt is-a Product, Watch is-a Product)
- **Extend functionality** — add new features to child without changing parent
- **Override** — change parent's behavior for specific cases
- **Maintainability** — change parent once, all children get update
- **Polymorphism** (later topic) — treat different children the same way

In your project:
- `Product` (parent) → all wearables have name, price, material
- `Clothing` (child of Product) → adds sizes, fabric type
- `Shirt` (child of Clothing) → adds collar style, sleeve length
- `Accessory` (child of Product) → adds color options, brand-specific fields

This structure makes adding new products (e.g., tie, glasses) easy — inherit from Product or Clothing.

## Detailed Explanation How Inheritance Works in Python (for Absolute Beginners)
Step-by-step:

1. **Basic Inheritance**
   ```python
   class Product:                    # Parent / Superclass
       def __init__(self, name, price):
           self.name = name
           self.price = price

       def display_info(self):
           return f"{self.name} - ₹{self.price}"

   class Shirt(Product):             # Child / Subclass
       pass                          # inherits everything

   shirt = Shirt("Blue Shirt", 999)
   print(shirt.display_info())       # Blue Shirt - ₹999
   ```

   Child gets all parent's attributes and methods automatically.

2. **Extending with New Attributes/Methods**
   ```python
   class Shirt(Product):
       def __init__(self, name, price, sizes, material):
           super().__init__(name, price)     # call parent's __init__
           self.sizes = sizes
           self.material = material

       def get_sizes(self):
           return ", ".join(map(str, self.sizes))
   ```

   - `super()` calls parent's method
   - Child adds its own stuff

3. **Overriding Methods** (change parent's behavior)
   ```python
   class Shirt(Product):
       def display_info(self):           # overrides parent's method
           return f"{self.name} - ₹{self.price} (Sizes: {self.get_sizes()})"
   ```

4. **Calling Parent Methods**
   Always use `super()` in `__init__` to avoid duplication.

5. **Multiple Inheritance** (advanced – one child, many parents)
   ```python
   class Discountable:
       def apply_discount(self, percent):
           return self.price * (1 - percent/100)

   class Shirt(Product, Discountable):   # inherits from two parents
       pass
   ```

   Not recommended early — can get complicated.

6. **Checking Inheritance**
   ```python
   print(isinstance(shirt, Shirt))     # True
   print(isinstance(shirt, Product))   # True (child is also parent type)
   print(issubclass(Shirt, Product))   # True
   ```

7. **Common Pitfalls for Novices**
   - Forgetting `super().__init__()` → parent attributes missing
   - Wrong order in multiple inheritance → method resolution order issues
   - Overriding without calling super → lose parent's logic
   - Thinking child changes parent's code → parent stays unchanged

## Syntax
```python
class Parent:
    def __init__(self, ...):
        ...

    def method(self):
        ...

class Child(Parent):               # inherit from Parent
    def __init__(self, ...):
        super().__init__(...)      # call parent constructor
        # add child-specific stuff

    def method(self):              # override
        super().method()           # optional: call parent's version
        # add child-specific behavior
```

## Sample Code Example (Practical for your project)
```python
# --- Mini Product hierarchy for your wearables app ---

class Product:
    def __init__(self, name, price, description=""):
        self.name = name
        self.price = price
        self.description = description

    def display_info(self):
        return f"{self.name} - ₹{self.price:.2f}\n{self.description}"

    def apply_discount(self, percent):
        return self.price * (1 - percent / 100)

class Clothing(Product):
    def __init__(self, name, price, sizes, material):
        super().__init__(name, price, f"Material: {material}")
        self.sizes = sizes

    def display_info(self):
        base = super().display_info()
        return f"{base}\nAvailable Sizes: {', '.join(map(str, self.sizes))}"

class Shirt(Clothing):
    def __init__(self, name, price, sizes, material, collar_type):
        super().__init__(name, price, sizes, material)
        self.collar_type = collar_type

    def display_info(self):
        base = super().display_info()
        return f"{base}\nCollar: {self.collar_type}"

# Usage
shirt = Shirt("Navy Blue Formal Shirt", 1499.99, [38, 40, 42], "Cotton", "Spread")
print(shirt.display_info())

print(f"After 10% discount: ₹{shirt.apply_discount(10):.2f}")
```

Run this — see how child classes build on parent without repeating code.

## 10 Interview Questions (Beginner Level)
1. What is inheritance in Python OOP?
2. What is the difference between parent class and child class?
3. What is the purpose of `super()`?
4. Can a child class override a parent's method?
5. What does `isinstance()` tell us about inheritance?
6. Explain "is-a" relationship with example.
7. What happens if you don't call super().__init__()?
8. What is multiple inheritance?
9. Why do we use inheritance instead of just copying code?
10. Give a real-world example of inheritance (like in your project).

## 10 Coding Interview Questions (Beginner Level)
1. Create `Animal` class with `eat()` method. Create `Dog` class that inherits and adds `bark()`.
2. Make `Vehicle` with `speed` and `move()`. Create `Car` that inherits and overrides `move()`.
3. Create `Shape` with `area()` method. Create `Rectangle` and `Circle` that inherit and implement area.
4. Make `Employee` with name, salary. Create `Manager` that inherits and adds bonus.
5. Create `BankAccount` with balance, deposit(), withdraw(). Create `SavingsAccount` that adds interest.
6. Make `Product` with name, price. Create `Clothing` that adds sizes and overrides display.
7. Use inheritance for `User` → `PremiumUser` that gets extra discount method.
8. Create `Person` with name, age. Create `Student` that adds grade and study() method.
9. Make base `Device` with power_on(). Create `Phone` and `Laptop` that inherit.
10. Implement `CartItem` base class → `PhysicalItem` (with weight) and `DigitalItem` (with download link).

## Links for YouTube Reference Videos
1. "Python OOP Tutorial 3 – Inheritance" – Corey Schafer  
   https://www.youtube.com/watch?v=Cn7O7q3E3Ls (full 20min) – Best in series, clear & practical.

2. "Inheritance in Python" – Programming with Mosh  
   https://www.youtube.com/watch?v=JeznW_7DlB0&t=1200s (inheritance section) – Simple explanations.

3. "Understanding Inheritance in Python" – freeCodeCamp  
   https://www.youtube.com/watch?v=Ej_02ICOIgs (watch inheritance part) – Visual examples.

4. "super() in Python Inheritance" – Telusko  
   https://www.youtube.com/watch?v=uoS7Yg3l3hA – 10min deep dive on super().

5. "Python OOP – Inheritance & super()" – Socratica  
   https://www.youtube.com/watch?v=apACNr7DC_s – 12min, great analogies.

**Tip for Novices**  
Inheritance feels powerful once you see it save code.  
Practice:  
1. Create `class Animal: def speak(self): print("Sound")`  
2. Create `class Dog(Animal): def speak(self): print("Woof")`  
3. `dog = Dog(); dog.speak()` → Woof  
4. Add `def eat(self): print("Eating")` to Animal → Dog gets it automatically  
5. Try `super()` in Dog's `__init__` if you add attributes

This is how you'll model Product → Clothing → Shirt hierarchy in your app.

Next file? Say: "next: python_oop_polymorphism.md" or any other (python_oop_encapsulation.md, flask_setup_routes.md, etc.)