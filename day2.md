
-----
🔹 1. **Class**
A class is a blueprint for creating objects. It defines a set of attributes and methods that the created objects (instances) can have.


Example:

    class Dog:
        species = "Canine"  # Class attribute
    
        def __init__(self, name, age):
            self.name = name  # Instance attribute
            self.age = age    # Instance attribute

🔹 2. **Object**
An object is an instance of a class. It represents a specific implementation of the class and holds its own data.


Example:


    dog1 = Dog("Buddy", 3)
    print(dog1.name)     # Output: Buddy
    print(dog1.species)  # Output: Canine


🔹 3. **Inheritance**
Inheritance allows a class (child class) to acquire properties and methods of another class (parent class), promoting code reuse.


Example:

    class Labrador(Dog):  # Single Inheritance
        def sound(self):
            print("Labrador woofs")


🔹 4. **Polymorphism**
Polymorphism allows methods to have the same name but behave differently based on the object’s context.

Example:

    class Beagle(Dog):
        def sound(self):
            print("Beagle barks")
    
    dogs = [Labrador("Buddy", 3), Beagle("Charlie", 5)]
    for dog in dogs:
        dog.sound()

🔹 5. **Encapsulation**
Encapsulation is the bundling of data (attributes) and methods within a class, restricting access to some components to control interactions.


Example:

    class Dog:
        def __init__(self, name, age):
            self.name = name          # Public attribute
            self.__age = age          # Private attribute
    
        def get_age(self):
            return self.__age
    
        def set_age(self, age):
            if age > 0:
                self.__age = age

🔹 6. **Abstraction**
Abstraction hides the internal implementation details while exposing only the necessary functionality. It helps focus on "what to do" rather than "how to do it."
or 
Abstraction hides the internal implementation details while exposing only the necessary functionality.


Example:

    from abc import ABC, abstractmethod
    
    class Dog(ABC):
        def __init__(self, name):
            self.name = name
    
        @abstractmethod
        def sound(self):
            pass



7. **Aggregation vs. Composition**
Aggregation: Represents a "has-a" relationship where the child can exist independently of the parent.

Composition: Represents a "has-a" relationship where the child cannot exist independently of the parent.

Aggregation Example:

    class Engine:
        def start(self):
            print("Engine started")
    
    class Car:
        def __init__(self, engine):
            self.engine = engine  # Aggregation
    
        def start(self):
            self.engine.start()
            print("Car started")
    
    e = Engine()
    c = Car(e)
    c.start()

In this example, the Engine object exists independently of the Car object.

-----


### 🔹 **Asynchronous Programming (async / await)**

* **Purpose**: Handle long-running tasks (like web requests or file I/O) **without blocking** the main thread.
* **Keywords**:

  * `async def`: Defines an asynchronous function.
  * `await`: Pauses the function until the awaited task is done.
* **Benefit**: Allows your program to **continue running other tasks** while waiting.

**Example**:

```python
import asyncio

async def greet():
    print("Hello")
    await asyncio.sleep(2)  # simulates a long task
    print("World")

asyncio.run(greet())
```

---

### 🔹 **Web Scraping Tools**

#### ✅ **BeautifulSoup (BS)**

* Used for parsing **HTML** and **XML** documents.
* Helps extract data from web pages.

```bash
pip install beautifulsoup4
```

**Example**:

```python
from bs4 import BeautifulSoup
html = "<h1>Hello</h1>"
soup = BeautifulSoup(html, 'html.parser')
print(soup.h1.text)  # Output: Hello
```

#### ✅ **Selenium**

* Used for **browser automation**.
* Good for scraping **JavaScript-heavy** or interactive websites.

```bash
pip install selenium
```

---

### 🔹 **Environment Management**

#### ✅ `venv` – Virtual Environment

* Keeps project libraries **isolated** from your system’s global Python packages.

```bash
python -m venv env
source env/bin/activate  # Mac/Linux
env\Scripts\activate     # Windows
```

#### ✅ `pip` – Package Installer

* Installs libraries from the Python Package Index (PyPI).

```bash
pip install numpy
```

* You can also save and install dependencies from a file:

```bash
pip freeze > requirements.txt
pip install -r requirements.txt
```

#### ✅ `poetry` – Dependency & Environment Tool

* More advanced than pip/venv.
* Manages **dependencies, environments, and publishing**.

```bash
pip install poetry
poetry init
poetry install
```

---

### ✅ Summary

| Tool/Concept    | Use Case                                |
| --------------- | --------------------------------------- |
| `async/await`   | Handle long-running code (non-blocking) |
| `BeautifulSoup` | Parse HTML/XML from web pages           |
| `Selenium`      | Automate browser actions (JS websites)  |
| `venv`          | Create isolated environments            |
| `pip`           | Install Python packages                 |
| `poetry`        | Advanced tool for managing projects     |




![image](https://github.com/user-attachments/assets/0dc9e39d-17dc-4957-82b2-4f9eb4070312)





