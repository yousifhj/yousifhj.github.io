---
layout: post
title:      "Class Methods and Instance Methods"
date:       2020-07-30 17:32:32 +0000
permalink:  class_methods_and_instance_methods
---


A few days ago I had my first project assessment. The first part of the assessment went well. I was able to answer all the questions that Jake had for me. I had spent a a little over a week preparing…I made sure I was familiar with all the concepts.

However, I had a hard time with the live coding. I froze. I was on the scraper class of my project and was asked to change the class method into an instance method. For some reason I wasn’t able to change my method. I knew exactly what I had to do but just couldn’t get myself to do it. I even said out loud:

*Class methods are methods that are called on a class and instance methods are methods that are called on an instance of a class. The difference is the word self.*

Above are two methods that are within the Beach Class. The first method is a class method and the second method is an instance method. The only difference in syntax is the self. in the first method. In Ruby, self is a context-sensitive keyword.

There are a few ways to call a class in Ruby. The first one we will look at is how to call on a class with a class method.

Beach.print_beach outputs “La Jolla Beach”

Beach.print_beach_location gives an error of an undefined method

The difference is when you are declaring and calling a class when you use a class method you can just use the dot syntax and have that method run. Whereas with an instance method you have to create a new instance of that class.

We can create a new instance of the beach class which will store it in the b variable. When we run the program we will get “La Jolla”

If I try to run b.print_beach I will receive an error of an undefined method.

A class method can be called on the class itself. The class method can be called on Beach.print_beach or whatever the name is. An instance method would require you to create a new instance of that class in order to be able to call it.

There is also another way which will work. The above line will give us the same result. However, the traditional way is to store the instance in a variable and that variable will be able to be used to call on it.

Class Methods are used when the functionality you are writing does not belong to an instance of that class. Instance Methods are used when you need to act on a particular instance of the class.


