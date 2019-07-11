---
title: Code Style & Best Practices
nav_previous: extending
nav_next: resources
layout: page
---
## Code Style

In general, it's considered good design to make your code as simple and expressive as possible. A lot of people want to write complex statements that show their prowess as a developer nu using niche, esoteric language features when simpler methods will work equally as well. I strongly encourage you to resist that urge. Your colleagues, collaborators, and future self will thank you when they see how simple and understandable your code is. 

Some tips to help you achieve this: 

* Use expressive names that describe what variables, functions, and files are for
* Each line of code should be simple, do only one thing. It's much better to break complex lines up into multiple smaller statements
* Group similar code into files, separate different code into their own files
* Pick a code style guide such as [PEP 8](https://www.python.org/dev/peps/pep-0008/) or the [Google Python Style Guide](https://www.python.org/dev/peps/pep-0008/) for your project
* Avoid *Premature Optimization*
* Focus on the minimum viable product
 
## Code Smells
Martin Fowler popularized a term among software developers known as *Code Smells*. Code smells are characteristics of source code that might indicate that there is a deeper underlying problem in your code or your development processes. It's important to note that a code smell doesn't necessarily mean that there is a problem, but is just an indication that you should take a moment to stop and think about your code. Here, I'll present a list of common code smells that indicate an opportunity to improve your code, based on the work presented in Robert C. Martin's book, *Clean Code*. 

### Code Design
A well designed code base is one that's easy to maintain, debug, and update. The way that we structure and organize our code can have a big impact on this.

#### Code Smells for Code Design
* Making any modifications requires that you make many small changes to many different parts of your code
* Making a change requires you to make changes in code that isn't directly related
* Code files contain code that does many different things
* Everything written in one giant file

### Functions 
Functions are one of the best ways that we can simplify our code, but it can be easy to overuse them or use them in ways that work against us. The key concept to remember is that a simple function is much easier to understand and debug than a complicated one. If you have a complex task that you need to solve, break it up into smaller manageable chunks. Each function you write should do only one thing. If you keep your functions small and targeted it will be much easier to track down and debug an issue.

#### Code Smells for Functions
* Functions with a lot of arguments
* Functions that are really long
* Functions that are deeply nested with conditionals
* Functions with many return statements

### Comments
Comments are something that are mistreated by a lot of people. Either they're hardly used at all, or they're used way too much. Neither case is desirable. 

No comments indicates that the code probably isn't ready for prime time. If the author hasn't taken the time to comment their code, they probably haven't taken the time to test it thoroughly.

If there are too many comments that simply state the obvious, we quickly learn to ignore them. Comments should be used sparingly but effectively, and always to convey the intent, meaning, or reasoning behind the code. Comments should always tell the reader things that the code cannot, and should do so in a thoughtful, concise manner.

Sometimes, comments are used as a means to make up for bad code. The code isn't understandable, so the author decorates it with comments to make up for this. The real solution to this problem is to simplify and improve the code itself.

#### Code Smells for Comments
* Comments that restate the obvious
* Really long comments
* Comments that don't use proper grammar, spelling, or sentence structure. 
* Commented out code

## Debugging

Sooner or later, you're going to write code that doesn't work the way you expected. Nobody writes perfect code the first time around, so debugging is a useful skill that is worth developing. Here are some tips for debugging your code:

1. Stop and think. Start by understanding the problem and when it happens. Gather information about the issue. Jot down some theories as to what might be going wrong.
2. Recreate the error. Under what conditions does the error happen? You won't know that you've fixed the problem until you're sure you can make it happen reliably.
3. If there is an error, read and understand the error message and stack trace. If you don't understand what the error message means, google it!
4. Check your assumptions. Print out the values of all the relevant variables around the issue.
5. Make one change at a time, then test to see the effect of your change.
6. Make notes and keep track of what you've done.
7. Talk through it with someone else. 
8. Learn to use a debugger.


 





