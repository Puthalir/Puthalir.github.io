Python
hello world!

----

🔹 **Variable**
A variable is a symbol (like x or y) used to represent a value that can change.

🔹 **Random Variable**
A random variable is a variable whose value is the outcome of a random process.

Example: Let X be the number of heads when flipping 2 coins.

🔹 **Experiment**
An experiment in probability is a process or action that leads to a result.

Example: Tossing a coin, rolling a die.

🔹 **Random Experiment**
An experiment where the outcome cannot be predicted with certainty.

Example: Rolling a die — you don’t know which number you’ll get.

🔹 **Outcome**
An outcome is a single possible result of an experiment.

Example: Getting a 5 when rolling a die.

🔹 **Basic Outcome**
Same as an elementary outcome — a single result in the sample space.

Example: Getting tails in one coin flip.

🔹 **Sample Outcome** / Sample Space
Sample Space (S): The set of all possible outcomes of an experiment.

Example: For a coin flip → S = {Heads, Tails}

🔹 **Discrete Random Variable**
Takes on countable values (usually whole numbers).

Example: Number of heads in 3 coin tosses → 0, 1, 2, 3.

🔹 **Continuous Random Variable**
Takes on infinite values in a range (like real numbers).

Example: Height, time, weight.

🔹 **Events**
An event is one or more outcomes of an experiment.

Example: Rolling an even number → {2, 4, 6}

🔹 **Function** / f(x)
A function assigns each input (x) to a specific output.

In probability: often refers to the Probability Function.

🔹 **Probability Mass Function** (PMF)
Used for discrete random variables. It gives the probability of each possible value.

Notation: P(X = x)

Example: P(X = 2) = 0.3

🔹 **Cumulative Distribution Function** (CDF)
Gives the probability that a random variable is less than or equal to a value.

Notation: F(x) = P(X ≤ x)

Used for both discrete and continuous variables.

🔹 **Probability Density Function** (PDF)
Used for continuous random variables.

Describes the likelihood of the variable falling within a range, not a specific point.

Notation: f(x)

🔹 **Set**
A collection of well-defined elements.

Example: A = {1, 2, 3, 4}

----

![image](https://github.com/user-attachments/assets/e8ab5b1d-e3aa-4d99-bf1e-840bec76c995)

----

🔹 **Set Operations**
Union (A ∪ B): All elements in A or B (or both)

Intersection (A ∩ B): Elements in both A and B

Difference (A − B): Elements in A but not in B

Complement (A′): All elements in the universal set not in A

----

🔹 1. **Python Function with Default Parameters**
Your code has a few issues — here’s the corrected version:

        def square(num, age=28):
            return num ** 2
        
        print(square(3))  # Output: 9
        

age=28 is a default parameter, but it's not used here.

num ** 2 squares the number.

🔹 2. Using **Lambda** Function
This is your code:


        addition = lambda x: x + x
        print(addition(5))  # Output: 10


This is an anonymous function using lambda.

lambda x: x + x means "double the input".

🔹 3. **OOP Concepts in Python**
Here are the main Object-Oriented Programming (OOP) concepts with short examples:

✅ **__init__** – Constructor
Used to initialize object properties.


        class Person:
            def __init__(self, name):
                self.name = name
        
        p = Person("Alice")
        print(p.name)  # Output: Alice


✅ **__del__** – Destructor
Called when an object is deleted.


        class Person:
            def __del__(self):
                print("Destructor called")
        
        p = Person()
        del p  # Will trigger the destructor


✅ **@decorator** – Decorators
Used to monitor/modify functions.


        def decorator(func):
            def wrapper():
                print("Before the function runs")
                func()
                print("After the function runs")
            return wrapper
        
        @decorator
        def greet():
            print("Hello!")
        
        greet()


✅ **Getter and Setter**

    class Student:
        def __init__(self):
            self._age = 0

    def get_age(self):
        return self._age

    def set_age(self, age):
        if age > 0:
            self._age = age

    s = Student()
    s.set_age(25)
    print(s.get_age())  # Output: 25

----

![image](https://github.com/user-attachments/assets/dbf62807-2d7b-4f88-ae6e-400ff6dc1a13)



----

Problem 

The manager of a factory claims that among his 400 employees.
‾ 312 got a pay rise last year
‾ 248 got increased pension benefits last year
‾ 173 got both pension benefits and pay rise last year
‾ 13 got neither

calculate the probability of.
a)	Getting a pay rise
Probability = 312 / 400 =0.78
b)	Not getting a pay rise
400 – 312 = 88
Probability = 88 / 400 = 0.22
c)	Getting both a pay rise and pension benefits
Probability =173 /400 = 0.432
d)	Getting no pay rise or benefit increase
Probability = 13 / 400 = 0.032
e)	Getting a pay rise or benefits
Probability = (312 + 248 – 173) / 400
= 387 / 400 = 0.967



1.	A production firm has produced 50 films in the past 5 years, directed by a team of 8 directors. Out of these 50 films, 35 became box office hits. 28 films won at least one major film award. 18 films achieved both a hit and won an award. 5 films neither became hits nor won awards.
Calculate the chance that a director picked at random:
a) Had a successful hit.
b) Missed out on a hit.
c) Was both a hit and won an award.
d) Was neither a hit nor won an award.
e) Was either a hit or won an award.
2.	An influencer is reviewing their posts reach and its responses in the past year. She saw 340 posts got at least 100 like 270 posts got at least 20 comments 190 posts got both at least 100 likes and at least 20 comments 40 posts got neither 100 likes nor 20 comments.

Calculate the probability that a randomly picked post:
a) Got at least 100 likes
b) Did not get at least 100 likes
c) Got both at least 100 likes and at least 20 comments
d) Got neither 100 likes nor 20 comments
e) Got either at least 100 likes or at least 20 comments
3.	A town Mayer is conducting a survey to find peoples interest in pets in the town of 1,000 households to build a pet park. 540 have a pet dog, 380 have a pet cat 220 have both a dog and a cat.
a) How many households have only a dog?
b) How many have only a cat?
c) How many have neither a dog nor a cat?
d) What is the probability that a randomly chosen household has a dog or a cat?

4.	For a university event 500 students registered for coding workshops 400 students registered for design workshops 250 students registered for both 150 students registered for neither.
Calculate the probability that a randomly picked student:
a) Registered for coding workshops
b) Did not register for coding workshops
c) Registered for both coding and design workshops
d) Registered for neither workshop
e) Registered for at least one workshop


5.	At a food festival 520 visitors tried Indian food 460 visitors tried Mexican food 300 visitors tried both 80 visitors tried neither.
Calculate the probability that a randomly picked visitor:
a) Tried Indian food
b) Did not try Indian food
c) Tried both Indian and Mexican food
d) Tried neither
e) Tried either Indian or Mexican food
