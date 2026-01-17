# python_file_io.md

## Definition of File I/O
**File I/O** (Input/Output) in Python means reading data from files (input) and writing data to files (output).  
It allows your program to save information permanently (on disk) and read it back later — instead of losing everything when the program ends.

For complete beginners with zero knowledge:  
Think of file I/O like writing in a notebook:  
- Writing (output): You open the notebook, write some notes (save data)  
- Reading (input): You open the notebook later and read what you wrote  

In your project:
- Save user measurements/profile to a file (so they don't re-enter every time)
- Load saved avatar data or cart items
- Write log of errors or successful orders
- Export user wishlist or generate report of popular sizes

Without file I/O, all data disappears when user closes the app — very frustrating!

## What and Why File I/O
**What**: Reading from and writing to files on your computer (text files, JSON, CSV, etc.).

**Why we need it**:
- Persist data between program runs (save user profile, cart, measurements)
- Load configuration/settings from files
- Export/import data (e.g., generate PDF of fabric booklet request)
- Log activities (debugging, analytics for brands)
- Read product catalog from CSV file
- Save generated avatar mesh or Gen AI textures

Files are how programs "remember" things forever.

## Detailed Explanation How File I/O Works in Python (for Absolute Beginners)
Step-by-step:

1. **Modes** (how you open the file)
   - `'r'` : read (default) – file must exist
   - `'w'` : write – creates new file or overwrites existing
   - `'a'` : append – adds to end of file (does not overwrite)
   - `'r+'` : read + write
   - Add `'b'` for binary (e.g., `'rb'`, `'wb'`) for images, etc.

2. **Best Way: `with` Statement** (recommended – auto closes file)
   ```python
   with open("data.txt", "w") as file:
       file.write("Hello from Python!")
   ```
   - File closes automatically when block ends (even if error)

3. **Writing to File**
   ```python
   with open("user.txt", "w") as f:
       f.write("Name: Vikram\n")
       f.write("Age: 25\n")
       f.write("City: Airoli")
   ```

   - `\n` = new line
   - Multiple writes → appends

   Append mode:
   ```python
   with open("log.txt", "a") as log:
       log.write("User logged in at 12:00\n")
   ```

4. **Reading from File**
   ```python
   with open("user.txt", "r") as f:
       content = f.read()          # reads entire file as one string
       print(content)
   ```

   Read line by line:
   ```python
   with open("user.txt", "r") as f:
       for line in f:
           print(line.strip())     # strip() removes \n
   ```

   Read all lines as list:
   ```python
   lines = f.readlines()   # ['Name: Vikram\n', 'Age: 25\n', ...]
   ```

5. **Reading + Writing Together**
   ```python
   with open("data.txt", "r+") as f:
       content = f.read()
       f.seek(0)               # go back to start
       f.write("Updated: " + content)
   ```

6. **Common File Types**
   - `.txt` : plain text
   - `.json` : structured data (very common in web apps)
   - `.csv` : comma-separated values (for spreadsheets)
   - `.png`/`.jpg` : images (use `'rb'`/`'wb'` mode)

7. **JSON Handling** (very important for real projects)
   ```python
   import json

   data = {"name": "Vikram", "age": 25, "city": "Airoli"}

   # Write to JSON
   with open("profile.json", "w") as f:
       json.dump(data, f, indent=4)   # indent makes it pretty

   # Read from JSON
   with open("profile.json", "r") as f:
       loaded = json.load(f)
       print(loaded["name"])   # Vikram
   ```

8. **Common Pitfalls for Novices**
   - Forgetting to close file → use `with` (auto closes)
   - Opening in wrong mode: `'r'` on non-existent file → FileNotFoundError
   - Writing numbers/strings without conversion: `f.write(25)` → TypeError (need str(25))
   - Not handling exceptions → program crashes on missing file
   - Encoding issues with special characters → use `encoding="utf-8"`

9. **Exception Handling with Files**
   ```python
   try:
       with open("missing.txt", "r") as f:
           print(f.read())
   except FileNotFoundError:
       print("File not found – creating new one...")
       with open("missing.txt", "w") as f:
           f.write("Default data")
   ```

## Syntax
```python
# Write
with open("file.txt", "w") as f:
    f.write("Line 1\n")
    f.write("Line 2")

# Read
with open("file.txt", "r") as f:
    content = f.read()
    # or
    lines = f.readlines()
    # or
    for line in f:
        print(line.strip())
```

## Sample Code Example (Practical for your project)
```python
# --- Mini user profile save/load for your app ---

import json

# Step 1: Save user profile to JSON
user_data = {
    "name": "Vikram",
    "age": 25,
    "height_cm": 175.5,
    "measurements": {"chest": 90, "waist": 80},
    "cart": ["shirt_001", "cap_005"],
    "preferences": {"premium": False, "booklet_requested": True}
}

try:
    with open("user_profile.json", "w", encoding="utf-8") as file:
        json.dump(user_data, file, indent=4)
    print("Profile saved successfully!")
except Exception as e:
    print("Error saving profile:", e)

# Step 2: Load profile back
try:
    with open("user_profile.json", "r", encoding="utf-8") as file:
        loaded_profile = json.load(file)
    
    print("\nLoaded Profile:")
    print("Name:", loaded_profile["name"])
    print("Height:", loaded_profile["height_cm"])
    print("Cart items:", loaded_profile["cart"])
    print("Booklet requested:", loaded_profile["preferences"]["booklet_requested"])

except FileNotFoundError:
    print("No saved profile found.")
except json.JSONDecodeError:
    print("Invalid JSON format in file.")
except Exception as e:
    print("Unexpected error:", e)
```

Run this twice — first time creates file, second time reads it. Change data and see updates.

## 10 Interview Questions (Beginner Level)
1. What is file I/O in Python?
2. Why do we use `with open(...)` instead of `open()` alone?
3. What are the main file modes ('r', 'w', 'a', 'r+')?
4. What happens if you open a non-existent file in 'r' mode?
5. How do you write multiple lines to a file?
6. Explain the difference between `read()`, `readline()`, and `readlines()`.
7. Why do we use `json` module for structured data?
8. What encoding should you use for files with special characters?
9. How do you handle FileNotFoundError gracefully?
10. What is the purpose of `finally` in file handling?

## 10 Coding Interview Questions (Beginner Level)
1. Write code to create a file "hello.txt" and write "Hello World" to it.
2. Read contents of "hello.txt" and print them.
3. Append current time to a log file every time program runs.
4. Save user name and age to a file, then read and print them.
5. Handle error if file doesn't exist when reading.
6. Write a list of products to a file, one per line.
7. Read a file and count how many lines it has.
8. Save dictionary to JSON file and load it back.
9. Create a function that writes error message to "errors.log" if something fails.
10. Read a file and print only lines that contain "shirt".

## Links for YouTube Reference Videos
1. "Python File I/O Tutorial for Beginners" – Corey Schafer  
   https://www.youtube.com/watch?v=Uh2ebFW8OYM (full 25min) – Best video, very clear and complete.

2. "Reading & Writing Files in Python" – Programming with Mosh  
   https://www.youtube.com/watch?v=9f4rvaYcJHI&t=3000s (first 15 minutes) – Simple, step-by-step.

3. "Python File Handling Tutorial" – freeCodeCamp  
   https://www.youtube.com/watch?v=Uh2ebFW8OYM&t=600s (watch file section) – Practical examples.

4. "Working with Files – open, read, write" – Telusko  
   https://www.youtube.com/watch?v=uoS7Yg3l3hA – 12min live coding.

5. "JSON File Handling in Python" – Socratica  
   https://www.youtube.com/watch?v=PZRI1IfStY0 – 10min, explains JSON saving/loading.

**Tip for Novices**  
File I/O is where your app becomes "persistent" — data survives restarts.  
Practice:  
1. `with open("test.txt", "w") as f: f.write("Hi")`  
2. `with open("test.txt", "r") as f: print(f.read())`  
3. Add more lines with "a" mode  
4. Try reading non-existent file → see error, then handle with try-except  
5. Save a dict to JSON and load it back

This is crucial for saving user profiles, carts, measurements, etc.

Next file? Say: "next: python_modules_packages.md" or any other (python_oop_classes.md, python_oop_inheritance.md, opencv_image_basics.md, etc.)