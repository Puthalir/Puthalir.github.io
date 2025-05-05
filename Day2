
-----
🔹 1. Class
A class is a blueprint for creating objects. It defines a set of attributes and methods that the created objects (instances) can have.


Example:

    class Dog:
        species = "Canine"  # Class attribute
    
        def __init__(self, name, age):
            self.name = name  # Instance attribute
            self.age = age    # Instance attribute

🔹 2. Object
An object is an instance of a class. It represents a specific implementation of the class and holds its own data.


Example:


    dog1 = Dog("Buddy", 3)
    print(dog1.name)     # Output: Buddy
    print(dog1.species)  # Output: Canine


🔹 3. Inheritance
Inheritance allows a class (child class) to acquire properties and methods of another class (parent class), promoting code reuse.


Example:

    class Labrador(Dog):  # Single Inheritance
        def sound(self):
            print("Labrador woofs")


🔹 4. Polymorphism
Polymorphism allows methods to have the same name but behave differently based on the object’s context.

Example:

    class Beagle(Dog):
        def sound(self):
            print("Beagle barks")
    
    dogs = [Labrador("Buddy", 3), Beagle("Charlie", 5)]
    for dog in dogs:
        dog.sound()

🔹 5. Encapsulation
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

🔹 6. Abstraction
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



7. Aggregation vs. Composition
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
