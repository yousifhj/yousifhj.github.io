---
layout: post
title:      "JavaScript Functions "
date:       2020-08-03 07:06:56 +0000
permalink:  javascript_functions
---

Functions are one of the fundamental building blocks in JavaScript. A function is a set of statements that preforms a task or calculates a value. Functions allow breaking a large program into smaller pieces. A function is also a reusable block of code. 

It allows for your code to be more manageable. Functions can split large programs into smaller pieces. It also allows for better organization of the program and it can improve code readability and understandability. 

In JavaScript, functions can be created inside the JavaScript script tag only. function is a reserved keyword of JavaScript .Use the keyword function with the name of the function

After the function name, open and close parentheses. After parenthesis, open and close curly braces. Within curly braces, write your lines of code from where the function starts and where ends are kept inside in curly braces

A function accepts one, zero or multiple parameters. Multiple parameters need to be separated by commas. 


A function **declaration** is a statement that describe what your code does. Declarations are hoisted, which means the function declaration will always be put at the scope which means calls can me made to the function even if it is declared somewhere later in the code.

*cookRice(2); 
function cookRice(qty) {
    return 'Rice'.repeat(qty)
}*

An alternative approach is use a function as a value or **expression** by assigning an anonymous function to a variable or parameter. The function doesn’t get created until that code is reached in the script. If called before hand an error will pop up. 


