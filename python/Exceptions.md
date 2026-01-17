# python_exceptions.md

## Definition of Exceptions
An **exception** in Python is an event that occurs during program execution when something goes wrong — like dividing by zero, accessing a missing file, or using a variable that doesn't exist.  
When an exception happens, Python stops normal execution and "raises" (throws) an exception object.

For complete beginners with zero knowledge:  
Think of an exception like a red warning light in your car:  
- Something bad happens (e.g., low fuel, flat tire)  
- The car doesn't crash — it shows a warning and stops or slows down  
- You (the driver) decide what to do next (fix it, ignore, pull over)  

In Python, exceptions are Python's way of saying: "Hey, something unexpected happened — here's what went wrong."

Examples from your project:
- User enters "abc" instead of number for size → ValueError
- Photo upload fails (file not found) → FileNotFoundError
- Division by zero in discount calculation → ZeroDivisionError
- Missing key in user profile dict → KeyError

## What and Why Exceptions
**What**: Exceptions are Python's built-in way to handle errors gracefully instead of crashing the whole program.

**Why we need exceptions**:
- Prevent program from crashing completely
- Show friendly error messages to users ("Please enter a valid number")
- Log errors for debugging
- Recover from problems (try again, use default value)
- Separate normal code from error-handling code (cleaner)
- Handle expected problems (invalid input, network failure, file missing)

In your app:
- Try to convert user input to int → catch ValueError if they type letters
- Open user photo → catch if file missing
- Access dictionary key → catch KeyError if key doesn't exist
- Without exceptions, your app would crash on every small mistake

## Detailed Explanation How Exceptions Work in Python (for Absolute Beginners)
Step-by-step:

1. **Exception is Raised**  
   When error happens, Python creates an exception object and stops normal flow:
   ```python
   print(10 / 0)   # ZeroDivisionError: division by zero
   ```

2. **try-except Block** (how you catch/handle exceptions)
   ```python
   try:
       num = int(input("Enter a number: "))
       print(10 / num)
   except ValueError:
       print("Please enter a valid number!")
   except ZeroDivisionError:
       print("Cannot divide by zero!")
   ```

   - `try`: code that might cause error
   - `except`: what to do if specific error happens
   - Multiple except blocks for different errors

3. **except without specific type** (catch all – use carefully)
   ```python
   except:
       print("Something went wrong!")
   ```

   Better to catch specific errors — catching everything hides real problems.

4. **else Block** (runs if NO exception occurred)
   ```python
   try:
       num = int("42")
   except ValueError:
       print("Invalid")
   else:
       print("Success! Number is:", num)
   ```

5. **finally Block** (always runs — cleanup)
   ```python
   try:
       file = open("data.txt")
   except FileNotFoundError:
       print("File not found")
   finally:
       print("Closing resources...")  # runs always
       # file.close() if open
   ```

6. **raise** (manually throw exception)
   ```python
   age = -5
   if age < 0:
       raise ValueError("Age cannot be negative!")
   ```

7. **Built-in Common Exceptions** (you'll see these a lot)
   - `ValueError`: Wrong value type (e.g., int("abc"))
   - `TypeError`: Wrong type in operation (e.g., "5" + 3)
   - `ZeroDivisionError`: Divide by 0
   - `KeyError`: Missing dict key
   - `IndexError`: List/tuple index out of range
   - `FileNotFoundError`: File doesn't exist
   - `NameError`: Variable not defined
   - `AttributeError`: No such method (e.g., list has no .upper())

8. **Exception Hierarchy**  
   All exceptions inherit from `Exception` class (you can catch `Exception` to get most errors).

9. **Common Pitfalls for Novices**
   - Bare `except:` → hides real errors (bad practice)
   - Catching too broad (`except Exception:`) → masks bugs
   - Not handling specific errors → crashes on expected issues
   - Forgetting to close files/resources → use `with` statement
   - Raising exceptions without message → hard to debug

## Syntax
```python
# Basic try-except
try:
    # risky code
except ErrorType:
    # handle it

# Multiple excepts + else + finally
try:
    # code
except ValueError:
    # handle value error
except ZeroDivisionError:
    # handle div by zero
except Exception as e:      # catch others, e = exception object
    print("Unexpected error:", e)
else:
    # runs if no exception
    print("Success!")
finally:
    # always runs (cleanup)
    print("Done.")
```

## Sample Code Example (Practical for your project)
```python
# --- Mini input validator & file handler for your app ---

def get_user_size():
    while True:
        try:
            size = int(input("Enter your size (38-44): "))
            if 38 <= size <= 44:
                return size
            else:
                print("Size must be between 38 and 44.")
        except ValueError:
            print("Please enter a valid number!")
        except KeyboardInterrupt:
            print("\nInput cancelled.")
            return None

# Example usage
user_size = get_user_size()
if user_size:
    print("Size saved:", user_size)

# File handling with exceptions
try:
    with open("user_measurements.txt", "r") as file:
        data = file.read()
        print("Measurements loaded:", data)
except FileNotFoundError:
    print("No saved measurements found. Starting fresh.")
    # create new file or use defaults
except PermissionError:
    print("Permission denied – cannot read file.")
except Exception as e:
    print("Unexpected error:", str(e))
finally:
    print("File operation complete.")
```

Run this — enter invalid input (letters), see how program doesn't crash.

## 10 Interview Questions (Beginner Level)
1. What is an exception in Python?
2. Why do we use try-except instead of letting program crash?
3. Name 5 common built-in exceptions.
4. What is the difference between `except Exception` and `except ValueError`?
5. What does `finally` block do?
6. Explain `else` block in try-except.
7. How do you raise a custom exception?
8. What is the purpose of `as e` in `except Exception as e`?
9. Why is bare `except:` considered bad practice?
10. Give an example of when to use `with` statement for files.

## 10 Coding Interview Questions (Beginner Level)
1. Write code that asks for number and handles ValueError if user enters text.
2. Create function that divides two numbers and handles ZeroDivisionError.
3. Try to open a file and print "File found" or "Not found" using try-except.
4. Ask user for age — raise ValueError if negative.
5. Use try-except-finally to always print "Done" after file operation.
6. Handle KeyError when accessing dict key that may not exist.
7. Write safe input function that keeps asking until valid integer.
8. Catch multiple exceptions in one block (ValueError + TypeError).
9. Use else block to print "Success" only if no error.
10. Create custom exception for invalid size input in your app.

## Links for YouTube Reference Videos
1. "Python Exceptions & Try-Except for Beginners" – Corey Schafer  
   https://www.youtube.com/watch?v=NG4jBfkU9hE (full 25min) – Best beginner video, very detailed.

2. "Try Except in Python – Error Handling" – Programming with Mosh  
   https://www.youtube.com/watch?v=NG4jBfkU9hE&t=600s (first 15 minutes) – Simple, clear examples.

3. "Python Exception Handling Tutorial" – freeCodeCamp  
   https://www.youtube.com/watch?v=PWdPLZvdO_I (watch exceptions section) – Practical demos.

4. "Understanding try-except-finally in Python" – Telusko  
   https://www.youtube.com/watch?v=uoS7Yg3l3hA – 12min live coding.

5. "Common Python Exceptions Explained" – Socratica  
   https://www.youtube.com/watch?v=PZRI1IfStY0 – 10min, shows ValueError, KeyError, etc.

**Tip for Novices**  
Exceptions prevent crashes — practice by intentionally causing errors:  
1. `print(10 / 0)` → see ZeroDivisionError  
2. Wrap it in try-except and print friendly message  
3. Try `int("abc")` → ValueError  
4. Handle it with except  
5. Always add finally: print("Cleanup done")

This is crucial for your app — users will type wrong things, files might be missing — exceptions keep it running smoothly.

Next file? Say: "next: python_oop_classes.md" or any other (python_oop_inheritance.md, python_file_io.md, python_modules_packages.md, etc.)