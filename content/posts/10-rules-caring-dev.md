---
title: 'Ten Tips for Becoming a More Caring Developer'
date: 2022-04-02T17:49:54-05:00
tags: [design, mindset]
featured_image: '/images/gardening-karolina-grabowska.jpg'
toc: true
draft: false
canonicalUrl: 'https://www.path-to-programming.tech/posts/10-rules-caring-dev/'
---

## 1. Leave the code better than you found it

To be more caring developers we must treat the code we write with respect and reverence. We must respect the future readers of your code. We often find ourselves placed with the task of maintaining legacy codebases. Some are prettier than others, but at the end of the day they are valuable to their users and serve a great purpose for the company. But, how can we improve the design, readability, and modularity of these codebases? We don't get there overnight&mdash;it takes time. Every time you work on a portion of the codebase find ways you can improve things. It could be as simple as renaming a variable or method. How can you make the code more readable for the next developer that comes along? How can you ensure that components are following SOLID principles and changes are easy to make. Composing software is not like constructing a building, but more like tending to a garden. Take the time to care for your codebase and remove weeds and thorns. The gardening metaphor is taken from The Pragmatic Programmer book.

New to refactoring? Get started by trying some [refactoring katas](https://kata-log.rocks/refactoring). Learn to identify [code smells](https://refactoring.guru/refactoring/smells) applying established [refactoring recipes](https://refactoring.guru/refactoring/what-is-refactoring)

## 2. Don't go fast, go well

As professional developers we don't have all of the time in the world when we are working on our feature changes. Although deadlines exist, sacrificing quality hurts in the long-term.

Codebases that are buried in technical debt and never receive any care are doomed to fail. By taking the time to refactor and carefully grow the design our software we actually end up saving time. Imagine the time you will save by having a codebase with clean code that can easily be understood by any newcomer!

## 3. Read your code from a different perspective

After you're done writing some code. Take a step back and ask yourself some questions:

- Does this make sense?
- Would I understand this if I read it tomorrow? Next week? Next year?
- How can I make this code more understandable?

Act as if you are new developer on the team and you have no idea what this system is doing. Would you be able to find out by reading the code or the tests?

Read your code from a different perspective and it will drive clarity into your solution.

## 4. Take small steps

Taking small steps while developing software is a key component to being able to be agile. TDD gives us a framework to get quick feedback. It can tell us if we are taking to large of steps or if we are on the right track. When you are feeling the pain of TDD creep up and the feedback cycles start to get longer and longer it is probably due to the fact that you are jumping to far ahead. Take incremental small steps&mdash;don't solve the whole problem all at once.

## 5. Avoid Scope Creep

Organizational habits are a key factor to being focused, productive, and on task.
When you are working on a feature you should only be focused on the problem at hand. You may come across code in other files that seems disorganized.
Should you:

- ignore it
- note it down somewhere (create a chore in the backlog)
- fix it right away

Well it depends. The common adage is that "You should only refactor code which is likely to change in the future". In that case, perhaps ignoring it is a viable solution. If the code you've found is closely related to the feature you are working on then feel free to change it. Lastly, if the code you've found is some bug or missed requirement it is best to create a new story in the backlog.

## 6. Try pair programming and get to know your pair

Being introduced to pair programming was one of the best things that ever happened to me. Not only has it made me a better developer, but a better person. Getting to know your pair is very important if you are going to have a sustainable relationship. Ask them how their weekend was. Ask about shared interests.

Share your favorite plugins, IDE shortcuts and CLI tools!

## 7. Think about the problem before diving into it

You should care about why you are doing something. Make sure to take time to understand the context around the problem you are trying to solve. Hopefully you have a clear and focused user story that accurately defines the scope you are working within. Make a list of tasks that you will need to complete to solve the problem at hand. Note down any questions that need to be answered by domain experts and shareholders. This list of tasks may change and evolve as you get deeper into the problem, but creating them upfront will help you focus on the problem.

## 8. Learn to identify code smells

A lot of new developers only focus on the technology stack. They often neglect design principles and refactoring. Technology comes and goes, but the skills of software design will be immensely important throughout your career. Code smells are one area you should focus on. It's useful knowing refactoring techniques, but if you aren't attuned to the kind of code that requires refactoring then those are somewhat useless. Take time to learn common code smells and how to make them better.

## 9. Take time to name things well

"There are only two hard things in Computer Science: cache invalidation, naming things, and off-by-1 errors." - Phil Karlton

"Any fool can write code that a computer can understand. Good programmers write code that humans can understand." - Martin Fowler

Naming things in software is extremely important. The names we choose should reflect the business language of our domain. This is where ubiquitous language comes into play. Ubiquitous language is a term that comes from Domain Driven Design. It is a design approach that involves building up a common, rigorous language between developers and users. The language should exist in every facet of the software, documentation, and in the conversations we are having with business experts.

Take the time to name things well.

## 10. Embrace code ownership

As I come from an XP background, I am fond of the idea that every developer on the team has ownership of the codebase. It is a developer's right to change code whenever they see something wrong. This may seem like a crazy idea, but in the world of XP where pair programming and incremental design are key practices it is not. Letting developers have ownership over a codebase will lead them to be more conscientious about the code they write. When they see an issue they can bring it up to the team, discuss it, and address the issue all in the same day. If this practice would be hard to fit into your team then try something small at first. If you have been meaning to get to some issue you see then write a story for it in your product management tool and get it assigned to your sprint. Taking on that work and reporting back the results to the team may encourage others to do the same. With the whole team behind this process you can start to clean things up and work more effectively together. If you see something, say something, and then do something about it.

[Cover Photo by Karolina Grabowska](https://www.pexels.com/photo/person-holding-green-plant-in-brown-clay-pot-4751970/)
