---
layout: post
title:  "The Anatomy of Object-Oriented Programming"
date:   2021-03-21 18:47:54 -0000
categories: OOP
---

> Object-Oriented Programming (OOP) is the core of software development in the modern world. Java and Python are the two most popular OOP languages used in the industry. As a learner who just starts to learn programming, you might have heard of the terms such as classes, instances and functions etc. But you might feel puzzled about how these terms build upon or connect with each other and what are the differences between class and objects/instances. I will use simplest words and intuitive examples to illustrate these concepts in this post.

### 1. Motivation
Why do we want to create our own classes? 
> "Classes provide a means of bundling data and functionality together. Creating a new class creates a new type of object, allowing new instances of that type to be made." - [Python Docs](https://docs.python.org/3/tutorial/classes.html)

It seems daunting to read the official definition from Python3 Doc. Let's first recall the reason why we want to create a method in python is to reduce duplicated work in our scripts. For instance, if we want to write a code chunk to calculate Fibonacci number, it's better to encapsulate the code chunk into a method so that we can just call the method anywhere we might need it instead of copying the code chunk over and over again. 

The similar motivation applies to classes. Using classes, we will be able to encapsulate similar ***behavior*** (so called functions) and ***information*** (so called data) together so that we can model the domain of your software more efficiently. This is what ***Abstraction*** is all about. 
> "Abstraction enables the commonality between similar but different things to be represented while details that vary between the things are factored out." - Credit to the UBC CPSC210 Lecture Note


### 2. Classes, Attributes and Functions
> ***Class = Data (also called Attributes) + Functions***

Now we understand that a class consists of data and functions. For instance, if we want to build a [Scrabble](https://www.wikiwand.com/en/Scrabble) game software, we might model the game by creating the main components such as players, game board, letter cards etc.

Let's take the ***player*** as an example. (See the code example below) 
- ***Attributes***: A player in the scrabble game might have some attributes such as `first_name`, `last_name`, `age`, `username` and `score` etc. When a new player (also called object. We will talk more about this in next section) is created in the game, we might assign different values to each of these attributes.
- ***Functions***: The player can perform many actions after entering the game. For instance, he/she can change their `username`, put a letter card on the game board, or just send a message to other players. These actions that a player can perform are called functions. A function may return something when it's called or just have an effect on other variables or other objects.


```python
class player():    
    def __init__(self, first_name, last_name, age, username):
        self.first_name = first_name
        self.last_name = last_name
        self.age = age
        self.username = username
        self.score = 0 # a new player has a score of 0.
        
    def change_username(self, new_username):
        self.username = new_username
        
    def put_letter_card(self, card, location):
        # If a couple of continuous letters in a row can make up an English word,  self.score will be increased by 1.
        # Otherwise, self.score remains unchanged.
        pass
    
    def send_msg(self, message):
        pass
```

Now, we've just created player class and it's ready to be used to create as many objects as you want. (We use objects and instances interchangeably.)

### 3. Objects (Instances)
> ***A class is a blueprint which we can use to create many instances based on that blueprint. You can also think of the relationship between a class and an instance as the relationship between cake mold and cake.***

An object is an instance of the class. Each object is associated with its own set of data and functions. Let's create two players `player1`, `player2`.

```python
player1 = player('frank', 'wang', '26', 'binarysearch')

player2 = player('mark', 'liu', '24', 'watermelon')

```

What happens in the line `player1 = player('frank', 'wang', '26', 'binarysearch')` is that `__init__` function will be called under the hood by the Python Interpreter to create the object for us. By saying an object being created, it means that a specific piece of memory will be allocated to store the information about the object in your computer. The values we passed into the brackets are called arguments, and the values of these arguments will be assigned to the corresponding attributes of the object. To put it simply, now, `player1`'s first name will be equal to `frank`, and `player1`'s last name will be now `wang` etc. If we print out `player1.fist_name`, the value `frank` stored in your memory will be printed out to the console.

Similarly, `player2` has same set of attributes (such as `first_name`, `age` etc.) and functions (such as `put_letter_card`, `change_username` etc.). But the values of these attributions belonging to `player2` are not the same as that of `player1` because when you run the line `player2 = player('mark', 'liu', '24', 'watermelon')`, a ***new*** piece of memory will be allocated for this object in your computer and this memory will specifically store the values for these attributes for `player2`. Same for the functions, even though two objects have functions with same name, they have different effects! For instance, when you call `player2.change_username("pineapple")`, `player2`'s username will be changed but it has nothing to do with `player1`'s attributes.

### 4. Takeaway points

- Class = Data + Functions
- A class is a cake mold whereas an object is the cake.
- An object is created under the hood when you run the line `player(...)`.
- Different objects created based on the same class have commonality such as attributions and functions but they are totally different set of things and each object is stored at different places in your memory. 

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
