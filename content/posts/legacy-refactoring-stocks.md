---
title: "Refactoring My Legacy"
date: 2023-11-21T12:01:48-05:00
tags: [design, legacy, refactoring, Java]
featured_image: ""
description: "My adventure of cleaning up the code I wrote as a young programmer."
draft: true
canonicalUrl: "https://www.pathtoprogramming.com/posts/legacy-refactoring-stocks/"
---

# The Spaghetti Code

I created Diamante Investments before I got my first software job. It's a stock portfolio manager desktop application built with Java Swing. At the time, I was interested in investing and reading stock charts.

The app’s capabilities are:

- Searching for stocks
- Viewing Stock Statistics
- Viewing Candlestick charts
- Adding stocks to watch list

[show muted demo of app or pics]

I remember at the time having an idea for a project that I could show to prospective employers, but having no idea how to do it. I had never used an API or a database before. All I had was an idea and a lot to learn on how to turn that idea into a reality.

# The Legacy Code Playground

![Working Effectively with Legacy Code](/images/working-legacy-code.jpg)

Years after I created Diamante Investments, I was reading Working Effectively with Legacy Code and I wanted a playground to practice some of the techniques I was learning about. This desktop app was the perfect candidate for legacy code refactoring. It was highly coupled, untestable, and had a terrible design. It’s a codebase written by a junior developer who was blindly copying code from articles and tutorials. I had no knowledge of how to produce maintainable and testable software. At that point in my journey, I was just happy to make it all work!

I decided to switch from SQLite to MySQL running in a docker container. Also, I added some UI tests using AssertJ Swing to verify I wasn’t breaking any functionality.

My main goal was just to have an opportunity to practice refactoring.

What did I learn from refactoring the stock app?

- How important readable variables, methods, & class names are
- How modular code leads to testable code
- How to refactor in small steps

# No Safety Net. Are you crazy?

[picture of tight rope walker]

Recently, I picked up where I left off and started refactoring the Stock Form and Stock Symbol classes.

I wanted to have a goal in this refactoring since it’s not advantageous to refactor code just to refactor. Luckily this app has several bugs that need to be addressed. However, due to the coupling, complexity, and clutter it is difficult to fix these bugs safely.

I used Naming as a Process as a framework to approach the refactoring.

Unfortunately, I had to abandon the UI tests since they don’t work on my Mac. Fortunately, it is possible to refactor code without tests. However, it requires a great deal of discipline and good tools.

# Refactoring the StockSymbol Class

![Diamante Investments](/images/during-hours-diamante-investments.png)

The StockSymbol class is a data class with way too many responsibilities. Within the constructor it scraps data from the web and calls an api for CSV data. With this kind of IO-related work it is quite difficult to test. Although I know the techniques to get this under test, I wanted to practice refactoring without tests. Many of the transformations I planned to make would be done via automated refactorings in IntelliJ.

## Remove Clutter

When dealing with a large class or method a good first step is to remove the clutter.

Clutter is any of the following:

- Dead code
- Comments that do not add value

Clutter is simple to get rid of because all you need to do is delete it. It’s very low risk and helps uncover other designs and patterns in your code.

I've already removed the clutter below, here's the [diff](https://github.com/SDiamante13/DiamanteInvestments/commit/16c97e6d7cfb077332d3fad78062cf7b2c274723).

{{< gist SDiamante13 5af398b1e6178dd6526c3ca89630df67 >}}

## IDE Autofixes

The next step is to leverage linting tools like SonarLint to autofix code smells in your code. Navigate to the next highlighted error with F2.

![Problem with if](/images/legacy-stock/autofix-if.png)

These warnings can be easily auto-fixed by using the Show Context Actions menu of IntelliJ (Option+Enter).

![Auto fix if](/images/legacy-stock/autofix-if-2.png)

To explore all the fixes I made check out the [diff.](https://github.com/SDiamante13/DiamanteInvestments/commit/90d273179c6c522a80922197e9a107b0eadf2172)

## Short Aside about Abstractions

Code should tell a story. Code is written so that other humans can read it. If that wasn’t the case then we’d all just write in assembly language. We have high-level languages that we can use to express our domain using abstractions.

![Chair](/images/chair.jpg)

Let’s say you and I are hanging out and I ask you to sit.

You: “Sit where?”

Me: “Sit on that wooden apparatus with 4 legs and a flat surface”

You: “Do you mean this chair?”

We use language to simplify concepts and objects that would otherwise need a full description. But if you and I both understand that a chair is an object that people sit down on, and we generally agree about what that entails then we can use this abstraction.

We should do the same while programming. Abstraction is an important concept in Object-Oriented Design. Let’s take these implementation details and replace them with an abstraction that describes a general behavior and not exactly how it’s being done.

## Extract Methods

After removing the clutter and cleaning some code up, we can start to extract methods.

The first step of extracting a method is finding what you need to extract. Developers naturally separate code into paragraphs (using whitespace). Code paragraphs can also exist within sections of curly braces such as try-catches, loops, or conditionals.

After finding the code paragraph and highlighting it, use the Extract Method refactoring command.

We are going to start from the bottom of the long method and work our way up. There are two reasons for that:

1. The more interesting stuff happens at the bottom of a method
2. Extracting methods from bottom to top will ensure the private methods are placed in the order of which they're called.

![Extract moving averages](/images/legacy-stock/extract-moving-avg.png)

The next choice we are tasked with is what to call this new method.

![Squishy](/images/legacy-stock/squishy.png)

Just name it applesauce for now.

This is the first stage of [Naming as a Process](https://www.digdeeproots.com/articles/on/naming-process/): **Obvious Nonsense**

Since we are not spending time to understand the code we don't have enough information right now to name this method. Applesauce is definitely not a good name, but it's better than what we had before which was nothing.

-----

Rename method to honest
Rename method to completely honest
autofixes (move closer to usages)
Regret about refactoring without tests
Include long methods talk from RSCC  
Conclusion
-----
