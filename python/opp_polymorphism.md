# python_oop_polymorphism.md

## Definition of Polymorphism
**Polymorphism** (from Greek: "many forms") is a core concept in Object-Oriented Programming (OOP) that allows objects of different classes to be treated as objects of a common parent class.  
The same method name can behave differently depending on which object calls it.

For complete beginners with zero knowledge:  
Think of polymorphism like a remote control:  
- You press the "Power" button  
- On TV → turns TV on/off  
- On AC → turns air conditioner on/off  
- On Fan → turns fan on/off  

Same button ("method name"), different devices ("objects"), different actions.  
That's polymorphism: same interface, different implementations.

In your project:
- Many classes inherit from `Product` (Shirt, Watch, Shoe, Cap)  
- All have a `display_info()` method  
- Calling `display_info()` on a Shirt shows sizes & collar  
- On a Watch shows strap & water resistance  
- Same method name, different behavior — that's polymorphism!

## What and Why Polymorphism
**What**:  
- Same method name works differently on different objects  
- Usually achieved through **inheritance** + **method overriding**  
- Lets you write code that works with many types without knowing exact type

**Why we need polymorphism**:
- Write flexible, generic code (e.g., loop over list of products and call `display_info()` on each)
- Reduce code duplication (one function handles all product types)
- Make code extensible (add new product type — no change to existing code)
- Support "duck typing" in Python ("if it walks like a duck and quacks like a duck...")
- Enable clean interfaces (e.g., all products have `get_price()`, `apply_discount()`)

In your app:
- Loop through cart items: `for item in cart: print(item.display_info())`  
  Works whether item is Shirt, Watch, or Shoe — no need for if-else per type

## Detailed Explanation How Polymorphism Works in Python (for Absolute Beginners)
Step-by-step:

1. **Method Overriding** (base of polymorphism)
   Child class redefines a method from parent.
   ```python
   class Product:
       def display_info(self):
           return "Generic Product"

   class Shirt(Product):
       def display_info(self):             # overrides parent's method
           return "Shirt with sizes and fabric details"

   class Watch(Product):
       def display_info(self):
           return "Watch with strap and water resistance"
   ```

2. **Polymorphic Behavior**
   ```python
   products = [
       Shirt("Blue Shirt", 999),
       Watch("Smart Watch", 4999),
       Product("Generic Item", 100)
   ]

   for p in products:
       print(p.display_info())
   ```
   Output:
   ```
   Shirt with sizes and fabric details
   Watch with strap and water resistance
   Generic Product
   ```

   Same `display_info()` call → different results based on actual object type.

3. **Python's Duck Typing** (polymorphism without strict inheritance)
   Python doesn't require inheritance — if object has the method, it works!
   ```python
   class Book:                        # no inheritance
       def display_info(self):
           return "Book: pages and author"

   products.append(Book("Python Book", 500))  # add anyway

   for p in products:
       print(p.display_info())        # works! (duck typing)
   ```

   "If it has `display_info()` method, treat it like a Product"

4. **Polymorphism with Functions**
   ```python
   def show_product_info(product):
       print(product.display_info())

   show_product_info(Shirt("T-Shirt", 599))   # calls Shirt version
   show_product_info(Watch("Analog", 2999))   # calls Watch version
   ```

5. **Polymorphism with Operator Overloading** (advanced intro)
   ```python
   class Price:
       def __init__(self, amount):
           self.amount = amount

       def __add__(self, other):          # overload +
           return Price(self.amount + other.amount)

   p1 = Price(100)
   p2 = Price(200)
   total = p1 + p2
   print(total.amount)   # 300
   ```

6. **Common Pitfalls for Novices**
   - Forgetting to override method → parent version called
   - Not using `super()` when needed → lose parent logic
   - Assuming strict type checking — Python is dynamic (duck typing)
   - Overriding without understanding parent behavior

## Syntax
```python
class Parent:
    def method(self):
        return "Parent behavior"

class Child(Parent):
    def method(self):               # override
        return "Child behavior"

# Polymorphic usage
obj = Child()
print(obj.method())                 # Child behavior

# List of mixed types
items = [Parent(), Child()]
for item in items:
    print(item.method())            # Parent → Child
```

## Sample Code Example (Practical for your project)
```python
# --- Polymorphic Product display for your app ---

class Product:
    def __init__(self, name, price):
        self.name = name
        self.price = price

    def display_info(self):
        return f"Product: {self.name} | Price: ₹{self.price:.2f}"

    def get_category(self):
        return "General"

class Clothing(Product):
    def __init__(self, name, price, sizes):
        super().__init__(name, price)
        self.sizes = sizes

    def display_info(self):                 # override
        base = super().display_info()
        return f"{base} | Sizes: {', '.join(map(str, self.sizes))}"

    def get_category(self):
        return "Clothing"

class Watch(Product):
    def __init__(self, name, price, water_resistant):
        super().__init__(name, price)
        self.water_resistant = water_resistant

    def display_info(self):
        base = super().display_info()
        wr = "Yes" if self.water_resistant else "No"
        return f"{base} | Water Resistant: {wr}"

    def get_category(self):
        return "Accessories"

# Polymorphic usage in cart
cart = [
    Clothing("Blue Shirt", 999.99, [38, 40, 42]),
    Watch("Smart Watch", 4999.00, True),
    Product("Generic Gift", 199.00)
]

print("Cart Summary:")
for item in cart:
    print(item.display_info())
    print("Category:", item.get_category())
    print("-" * 40)
```

Run this — see how one loop handles different product types perfectly.

## 10 Interview Questions (Beginner Level)
1. What is polymorphism in Python?
2. How is polymorphism achieved in Python?
3. What is method overriding?
4. Explain duck typing with example.
5. Why is polymorphism useful in OOP?
6. Does Python require inheritance for polymorphism?
7. What is the benefit of overriding `__str__` in polymorphism?
8. Give an example of polymorphism in real code.
9. What happens if a child class doesn't override a method?
10. Explain "same interface, different implementation".

## 10 Coding Interview Questions (Beginner Level)
1. Create `Shape` base class with `area()` method. Create `Circle` and `Rectangle` that override it.
2. Make `Animal` with `speak()`. Create `Dog`, `Cat`, `Bird` that override speak().
3. Create `Payment` base with `process()` method. Create `CardPayment` and `UPIPayment` subclasses.
4. Build `Vehicle` with `move()`. Create `Car` ("Driving...") and `Plane` ("Flying...").
5. Make `Employee` with `calculate_salary()`. Create `Developer` (base + bonus) and `Manager` (base + team bonus).
6. Create `Product` with `get_details()`. Create `Book` (adds author) and `Shirt` (adds sizes).
7. Write function `show_info(obj)` that calls `obj.display_info()` — works for any class with that method.
8. Use polymorphism to calculate total price of mixed products.
9. Create base `Logger` with `log()` — create `FileLogger` and `ConsoleLogger`.
10. Implement `Drawable` with `draw()` — create `Circle`, `Square` that inherit and implement.

## Links for YouTube Reference Videos
1. "Python OOP Tutorial 5 – Polymorphism" – Corey Schafer  
   https://www.youtube.com/watch?v=ZDa-Z5JzLYM&t=1200s (polymorphism part) — Excellent, clear examples.

2. "Polymorphism in Python Explained" – Programming with Mosh  
   https://www.youtube.com/watch?v=JeznW_7DlB0&t=1800s (polymorphism section) — Simple & practical.

3. "Understanding Polymorphism in Python" – freeCodeCamp  
   https://www.youtube.com/watch?v=Ej_02ICOIgs (watch polymorphism part) — Visual demos.

4. "Method Overriding & Polymorphism" – Telusko  
   https://www.youtube.com/watch?v=uoS7Yg3l3hA – 10min live coding.

5. "Python Polymorphism & Duck Typing" – Socratica  
   https://www.youtube.com/watch?v=apACNr7DC_s – 12min, great analogies.

**Tip for Novices**  
Polymorphism feels magical at first — it's the power of "same name, different action".  
Practice:  
1. Create `class Animal: def speak(self): print("Sound")`  
2. `class Dog(Animal): def speak(self): print("Woof")`  
3. `class Cat(Animal): def speak(self): print("Meow")`  
4. `animals = [Dog(), Cat(), Animal()]`  
5. `for a in animals: a.speak()` → Woof, Meow, Sound

This is how your cart can handle Shirt, Watch, Cap — all with one `display_info()` call.

Next file? Say: "next: python_oop_encapsulation.md" or any other (python_file_io.md, flask_setup_routes.md, etc.)