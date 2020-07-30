---
layout: post
title:      "JavaScript at it’s finest"
date:       2020-07-30 17:42:10 +0000
permalink:  javascript_at_it_s_finest
---


I don’t think I’ve ever been as frustrated as I am. I have tried sooooo many different ways to get my application to run properly and I can’t seem to get it to do what I want it to do. I can’t wait until I have the debugging skills that that Nancy(Cohort Lead) has. It’s definitely something to look forward to. I figured the best thing to do is leave my code alone for a bit. So, Here I am.

Below are a few of the things that I’ve learned about JavaScript

## jQuery
jQuery is a JavaScript library designed to simplify HTML DOM tree traversal and manipulation, as well as event handling, CSS animation, and Ajax. It’s basically used to connect with HTML elements in the browser via the DOM. The Document Object Model is the method by which Javascript and jQuery interact with the HTML in the browser.

### JavaScript Prototype

Javascript only has one construct: objects. All JavaScript objects inherit properties and methods from a prototype:

*Data objects inherit from Data.prototype
Array objects inherit from Array.prototype 
People object inherit from People.prototype *

Every object has a private property that holds a link to another object called its prototype. That prototype also has a prototype of its own, until an object is reached with null as its prototype. Null has no prototype, and acts as the final link in this prototype chain.

### JavaScript(ES6) Class

Classes are basically syntactical sugar over JavaScript’s existing prototype-based inheritance. It’s a blueprint from which individual objects are created. Classes provide a simpler and clearer syntax to create objects and deal with inheritance. One way to define a class is by using a class declaration. A class can also be defined by a class expression. Class expressions can be either named or unnamed. The name given to a named class expression is local to the classes body.
named class: 

*var puppy = class Dog {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
};*

Both named and unnamed start with a variable name. The only difference is the named class has the class name.

*unnamed class: 
var cat = class {
  constructor(name, age) {
    this.name = name;
    this.age = age; 
  }
};*

### JavaScript Scope

The scope of a variable or a constant determines where that constant/variable is accessible . Variables that are declared by let or const; the scope is limited to the block in which they are defined.

*function start() { 
  const message = "Hello World";
}*

The scope of the constant (above) is limited to the block is which its defined it will not be accessible outside of the start function. The same would be true if a variable or constant is declared in an if block. Variables declared within a JavaScript function become local to the function. A variable declared outside a function becomes global. The global variable has global scope; which can be accessed by all scripts and functions.

### JavaScript Nested Function

Creating a function inside another function is called nested functions in javascript. A function will always have access to the outer scope.

innerFunction is a nested function that is inside of parentFunction. Variable a, is located in the outer scope of innerFunction which is a local variable. Returning a + b when innerFunction is called 8 will be returned. The innerFunctuon has access to the a variable. It will always have access to the outer scope. It also has access to the global scope.

### The Module Pattern
The Module design pattern is one of the most used design patterns for keeping particular pieces of code independent from each other. Modules allow programmers to break up different parts of code to make it easier to maintain and reason about. Modules can also provide encapsulation which can protect properties and functions from being accessed from other parts of the code.

### Hoisting

Variable declarations and function declarations are processed before any code is executed. Declaring a variable or a function anywhere in the code is equivalent to declaring it at the top. This means that a variable and functions can be used before they are declared. This behavior is called hoisting. The declaration is moved to the top. Variable definitions are when you assign a value to a variable, which aren’t hoisted to the top.

### Callback Function

Call backs are tremendously useful and give programmers a lot of flexibility as well as extendability. JavaScript allows you to define functions as variables. They are no different than any other objects. The only difference is that you can invoke them. This allows programmers can take advantage of the feature of the language to pass them around and allow us to gain some flexibility.

Above are just a few of the things I’ve learned over the past month. There's so much to master.

Thanks for reading!
