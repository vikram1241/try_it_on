# python_oop_encapsulation.md

## Definition of Encapsulation
**Encapsulation** is one of the four fundamental principles of Object-Oriented Programming (OOP).  
It is the practice of **hiding the internal details** (data and implementation) of an object and providing a controlled way to access or modify them — usually through **public methods**.

For complete beginners with zero knowledge:  
Think of encapsulation like a medicine capsule or a vending machine:  
- Inside the capsule/machine: important/hidden medicine/mechanism (private data)  
- Outside: you see only buttons/labels (public interface)  
- You interact only through the buttons → you can't directly open the capsule or reach inside the machine  

In Python, encapsulation means:  
- Keep some data "private" (hidden from direct outside access)  
- Provide public methods to safely read/change that data  
- Protect the internal state from accidental or incorrect changes

This is how real apps stay safe and maintainable.

## What and Why Encapsulation
**What**:  
- Bundle data (attributes) and methods that operate on that data inside a class  
- Restrict direct access to some attributes (make them "private")  
- Expose only necessary parts through public methods (getters/setters)

**Why we need encapsulation**:
- **Data protection** — prevent invalid values (e.g., negative age, impossible height)
- **Hide complexity** — user of class doesn't need to know how data is stored
- **Control access** — allow read-only, write-only, or validated changes
- **Maintainability** — change internal implementation without breaking outside code
- **Security** — sensitive data (passwords, measurements) not directly changeable
- **Reduce bugs** — fewer places where data can be accidentally corrupted

In your project:
- `User` class hides raw measurements — only allows valid updates via method
- `Cart` class hides internal list — only exposes `add_item()`, `remove_item()`, `get_total()`
- `Product` hides price calculation logic — provides `get_final_price()` after discount

Without encapsulation, anyone could do `user.age = -100` or `cart.items = None` — breaking your app.

## Detailed Explanation How Encapsulation Works in Python (for Absolute Beginners)
Python doesn't have strict "private" like Java/C++ — it uses **convention** and **name mangling**.

1. **Public, Protected, Private by Convention**
   - Public: `self.name` — anyone can access
   - Protected: `self._name` (single underscore) — convention: "don't touch directly, for internal use"
   - Private: `self.__name` (double underscore) — name mangling: Python changes name to `_ClassName__name` → hard to access from outside

   ```python
   class User:
       def __init__(self, name, age):
           self.name = name               # public
           self._age = age                # protected (convention)
           self.__password = "secret123"  # private (mangled)

       def get_age(self):
           return self._age

       def set_age(self, new_age):
           if new_age > 0:
               self._age = new_age
           else:
               print("Age cannot be negative!")

       def show_password(self):
           return self.__password  # accessible inside class
   ```

   Outside class:
   ```python
   u = User("Vikram", 25)
   print(u.name)           # OK: Vikram
   print(u._age)           # Works but discouraged: 25
   # print(u.__password)   # ERROR! AttributeError
   print(u._User__password) # Works but bad practice: secret123
   ```

2. **Getters & Setters** (controlled access)
   Use methods to read/write private/protected attributes.
   ```python
   u.set_age(26)           # OK
   u.set_age(-5)           # Prints warning, doesn't change
   ```

3. **Property Decorator** (clean way – looks like attribute but uses methods)
   ```python
   class User:
       def __init__(self, name, age):
           self._age = age

       @property
       def age(self):                  # getter
           return self._age

       @age.setter
       def age(self, value):           # setter
           if value > 0:
               self._age = value
           else:
               raise ValueError("Age cannot be negative")

   u = User("Vikram", 25)
   print(u.age)          # 25 (calls getter)
   u.age = 26            # calls setter
   # u.age = -5          # raises ValueError
   ```

   Looks like normal attribute access, but with validation!

4. **Encapsulation Levels Summary**
   - No underscore: public (everyone can access)
   - Single underscore: protected (convention: internal use only)
   - Double underscore: private (name mangling – hard to access outside)

5. **Common Pitfalls for Novices**
   - Thinking double underscore makes attribute truly private → can still access with `_Class__attr`
   - Not using properties → direct access bypasses validation
   - Overusing private — most attributes can be public if no validation needed
   - Forgetting `self.` when using attributes inside methods

## Syntax
```python
class ClassName:
    def __init__(self):
        self.public_attr = "visible"
        self._protected_attr = "internal"
        self.__private_attr = "hidden"

    @property
    def protected_attr(self):
        return self._protected_attr

    @protected_attr.setter
    def protected_attr(self, value):
        # validation here
        self._protected_attr = value
```

## Sample Code Example (Practical for your project)
```python
# --- Encapsulated User & Cart classes ---

class User:
    def __init__(self, name, email):
        self.name = name
        self._email = email          # protected
        self.__password = None       # private
        self.__measurements = {}     # private dict

    # Getter for email (read-only)
    @property
    def email(self):
        return self._email

    # Setter with validation
    @email.setter
    def email(self, new_email):
        if "@" in new_email:
            self._email = new_email
        else:
            raise ValueError("Invalid email format")

    # Method to safely update measurements
    def add_measurement(self, key, value):
        if key in ["chest", "waist", "inseam"] and value > 0:
            self.__measurements[key] = value
        else:
            print("Invalid measurement")

    def get_measurements(self):
        return self.__measurements.copy()  # return copy to protect original

class Cart:
    def __init__(self):
        self.__items = []          # private list

    def add_item(self, product):
        self.__items.append(product)
        print(f"Added {product['name']}")

    def remove_item(self, product_name):
        self.__items = [item for item in self.__items if item["name"] != product_name]

    @property
    def item_count(self):
        return len(self.__items)

    def get_total(self):
        return sum(item["price"] for item in self.__items)

# Usage
vikram = User("Vikram", "vikram@example.com")
vikram.add_measurement("chest", 90)
vikram.add_measurement("waist", 80)

print("Measurements:", vikram.get_measurements())

cart = Cart()
cart.add_item({"name": "Shirt", "price": 999})
cart.add_item({"name": "Cap", "price": 499})

print("Items in cart:", cart.item_count)
print("Total: ₹", cart.get_total())

# Try direct access (won't work easily)
# print(vikram.__password)      → AttributeError
# print(vikram._User__password) → possible but bad practice
```

Run this — try direct access to `__measurements` or `__items` → see protection.

## 10 Interview Questions (Beginner Level)
1. What is encapsulation in OOP?
2. How does Python implement encapsulation (convention)?
3. What is the difference between public, protected, and private attributes?
4. What is name mangling and why is it used?
5. Explain `@property` and `@<name>.setter` decorators.
6. Why should we use getters/setters instead of direct attribute access?
7. Can you access a private attribute from outside? How?
8. What is the benefit of encapsulation in a real project?
9. Give an example of when to use private attributes.
10. What happens if you don't use encapsulation?

## 10 Coding Interview Questions (Beginner Level)
1. Create `Person` class with private `__age` and getter/setter with validation (age > 0).
2. Make `BankAccount` class with private `__balance` and methods deposit/withdraw.
3. Create `Product` with private `__price` and property to get/set price (prevent negative).
4. Build `User` class with private `__password` and method to change password with confirmation.
5. Implement `Cart` with private `__items` list and public methods to add/remove/get total.
6. Create `Student` with private `__marks` dict and method to add mark with validation (0-100).
7. Make `Temperature` class with private `__celsius` and properties for celsius/fahrenheit.
8. Create `Book` with private `__pages` and getter that returns read-only value.
9. Implement `Logger` with private `__logs` list and method to add/log messages.
10. Create `Avatar` class with private `__measurements` dict and safe add/get methods.

## Links for YouTube Reference Videos
1. "Python OOP Tutorial 4 – Encapsulation & Properties" – Corey Schafer  
   https://www.youtube.com/watch?v=JFll6w2pX4Q (full 20min) — Best explanation of properties & private attributes.

2. "Encapsulation in Python OOP" – Programming with Mosh  
   https://www.youtube.com/watch?v=JeznW_7DlB0&t=2400s (encapsulation section) — Simple & practical.

3. "Python Properties & Getters/Setters" – freeCodeCamp  
   https://www.youtube.com/watch?v=Ej_02ICOIgs (watch properties part) — Visual examples.

4. "Private Variables & Name Mangling in Python" – Telusko  
   https://www.youtube.com/watch?v=uoS7Yg3l3hA – 10min deep dive on __private.

5. "Understanding Encapsulation in Python" – Socratica  
   https://www.youtube.com/watch?v=apACNr7DC_s – 10min, great analogies for hiding data.

**Tip for Novices**  
Encapsulation is about "safety and control".  
Practice:  
1. Create `class BankAccount: def __init__(self): self.__balance = 0`  
2. Add `def deposit(self, amount): if amount > 0: self.__balance += amount`  
3. Add `def get_balance(self): return self.__balance`  
4. Try `account.__balance = -100` → doesn't work directly  
5. Use getter/setter — see how you control changes

This protects important data in your app (user measurements, cart contents, passwords).

Next file? Say: "next: python_oop_encapsulation.md" (wait — you already asked for encapsulation, so perhaps "next: python_file_io.md" or "flask_setup_routes.md" or any other remaining concept)