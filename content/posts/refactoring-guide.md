---
title: 'Refactoring Guide'
date: 2022-03-30T21:02:50-04:00
tags: [design, refactoring]
featured_image: ''
description: 'This post will explore common code smells and the relative refactorings needed to improve the current design.'
draft: true
canonicalUrl: 'https://www.path-to-programming.tech/posts/refactoring-guide/'
---

# What is refactoring?

Refactoring is a term coined by Ralph Johnson. The term has its origins in mathematics. [reword - lookup factoring and have the math part be one sentence stand alone]Just as you would reduce the terms of a mathematical function, in programming you can change the design of code without changing its behavior.

Martin Fowler wrote a book called "Refactoring Improving the Design of Existing Code" that many of the ideas I will discuss in this post will refer to. In his book, he defines refactoring as "the process of changing a software system in such a way that it does not alter the external behavior of the code yet improves its internal structure."

There are two types of qualities in programming. One type is external quality. External quality means that the code is doing what it was designed to do. When a user interacts with the software and is generally satisfied by its behavior this could point to a high degree of external quality. When a developer fixes a bug in their software they are improving the external quality of the software.

The other type of quality is internal quality. This kind of quality usually affects the developers of the codebase. Is the system designed well? Is the code readable and easy to understand? How easy is it to introduce a behavior change into the system?

Refactoring is focused on improving the internal quality of a system. A refactoring can be as simple as renaming a variable, method, or class to be more descriptive and intention revealing. Even moving a private method closer to where it's called from can be considered a refactoring. Refactoring is what we do to achieve clean code and progress towards an evolutionary design.

# Why should I refactor my code?

As our code evolves and requires more capabilities it can get rather complex and hard to understand. Sometimes the changes we need to add to the system are not easy to make given the current design. What if there was a way we could restructure the code to make the feature easier to add? Sometimes the best occasion to refactor is right before adding some new behavior. Kent Beck has a great take on this: "First make the change easy, then make the easy change".

Refactoring allows us to grow our design over time. We can start out with a simple design and as complex behaviors are introduced to the system we can continue reshaping the design to maintain this simple nature.

# Welcome to the wonder world of refactoring!

If this is your first introduction to refactoring, I'm sure that you've already used some of these refactoring before without even knowing it. In this post we will learn names and steps to some common refactorings. We will explore how to safely refactor your code. Add more to this!

# What if I mess up? How do I protect against regressions?

When first diving into the pool of refactoring it can be quite intimidating. You could find yourself in a codebase that is crucial for the business you work for and introducing any bugs into the system could cost them huge sums of money. We should never wander into refactoring, but instead take a mindful approach and follow a safe strategy for accomplishing your task of improving the design of the code.

One of the best safe guards against regressions is having an automated test suite that can be run after making any refactorings. You should have tests that you trust to reflect the behavior of the system. Another safety measure while refactoring is to utilize an IDE and use the built-in refactoring tools. The refactoring methods that an IDE like IntelliJ has can handle your basic refactorings. It will not always cover every situation, but I would learn those tools and opt for those first as they can reduce the time it takes and protect against mistakes that humans like to make.

# Common Refactorings

Let's look at some basic refactorings that you may find yourself using in the future. Some of these refactoring require a certain situation and can be applied when the circumstances exist.

## Extract method

Extract method is the act of taking some code and calling from a private method within the same class. This can a great way to have your code comment itself.

Add example here?

void sendInvoice(Invoice invoice) {

}

## Rename Method

Naming is hard right? The rename method refactoring can be applied when you discover a method that can be named better. The names we choose for variables, methods, and classes should be intention revealing and give the reader a sense of that scope's responsibility.

## Replace Temp with Query

## Form Template Method

## Inline Method

## There's more where that came from

Fowler's Refactoring book has 72 refactorings and there are other modern ones that have been introduced by others. We will look at some other refactoring in this guide as well.

# What to look for? Code Smells

It's nice to learn some of the solutions, but what are the problems? In what situations, should one apply these different refactorings? That's where the concept of code smells come into play.

A code smell is a structure of code that is violating some design principle. Code smells are rather subjective, but there are some common code smells that you should be aware of.

## High cyclomatic complexity

## Feature Envy

## God object

## Primitive Obsession

## Data Clumps

# Small steps (commit often)

Refactoring should be approached in a systematic way. Early on in my career, I embraced refactoring and attempted it in a variety of production codebases. Often I encountered codebases with fragile tests that were testing the implementation of the code and had several mocks that made refactoring difficult. As a result, my pair and I would usually spend several days in a broken state. One time we even deleted the tests and rewrote them after we restructured the code. Although this can be necessary at times, it isn't the easiest way to approach refactoring.

While refactoring you should make commits often and run the test even more often. I like to think of git commits like a checkpoint in a video game. When you just made a great refactorings and improved the structure of the code you should commit so you have a checkpoint to go back to if the next move is not as successful.

Here's the strategy I normally employ while refactoring:

1. Identify a code smell that I would like to get rid of
2. Attempt to refactor the code using my IDE's refactoring tools
3. If I had to make any manual moves, then I run the tests
4. If the next refactoring I am attempting is rather complex then I commit.

I used to run the tests after every move I make, but I have been trying to utilize my IDE as much as possible and I've learned to trust it.

# When should I refactor? Refactoring workflows (Credit Martin Fowler talk)

# Project challenges

A question I hear often is "How do I convince my manager to allow me to refactor the code?".

# When do I know when to stop refactoring?

Refactoring is an ongoing task and if not done with mindfulness can spiral out of control. You can definitely refactor code too much and start get less value out of it; in some cases you may even make the software worst.

So, when should you stop refactoring? Have a goal in mind and stop refactoring when you've accomplished that goal. If your refactoring kicked off because you are introducing a new change to a complex system, then your goal would most likely be to make the new change easy to add. Sometimes you are refactoring just to make your code cleaner. For this workflow, I would suggest time boxing your refactoring. Commit to spending 30 minutes refactoring and stop when the time is over.

# The different hats metaphor ( Refactoring Hat vs. Adding Behavior Hat)

# How do I practice refactoring?

# How do I refactor code without tests?

# Leveraging the IDE

# Examples
