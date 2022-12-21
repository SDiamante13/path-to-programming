---
title: "Take smaller steps with test driven development"
date: 2022-12-21T12:00:00-04:00
tags: ["tdd", "refactoring", "design"]
featured_image: "/images/footprints.jpg"
description: ""
draft: false 
canonicalUrl: "https://www.path-to-programming.tech/posts/tdd/"
---

# You can stop improving your debugging skills


When I first started coding in college, I remember how hard programming was in those days. One project, we were tasked to build KABOOM!

{{< youtube ekMImsw3Z7Y >}}

Back then, I was not good at design. We're talking "death from a 1000 if's" here. My professor encouraged everyone to write many comments. Now I understand why... our code was impossible to read! Back then, no ones code read like a book.
The night before the due date a few of us from class were working together. I had so many conditionals in my code I couldn't keep all the logic of the program in my brain. I was not able to compile my program and was completely stuck. I got help from a classmate, and he helped me debug the problem. Back then debugging was a crucial skill to learn. After you get the main process it seems simple. Some people take great pride in their ability to set up breakpoints and track a bunch of variables. However, I was never that good at it. It turns out I don't need to be a virtuoso debugger. I have TDD.

> I'm not a great programmer, I'm a good programmer with great habits - Kent Beck


# TDD - the great equalizer

Test driven development is an engineering practice that helps me write better code. Not only does writing the tests first allow you to have testable code, but you'll take smaller steps and be able to iterate on your design. 

TDD is about gaining control. The feedback loop that TDD gives you yields so much power. At any moment you can verify your software works the way you expect it to. These automated tests serve as the safety net when we are evolving our software design. Refactoring without tests is very risky. TDD gives developers the confidence they need to refactor at any moment. 

But that's enough theory. The best way to learn TDD is to practice it.

# Leap Year TDD Kata

To learn the rhythm and flow of TDD we are going to work on a small exercise together. 

## Business use case

> "It takes approximately 365.25 days for Earth to orbit the Sun — a solar year. We usually round the days in a calendar year to 365. To make up for the missing partial day, we add one day to our calendar approximately every four years. That is a leap year." - NASA

![Alt Text](/images/earth.jpg)

Write a function that returns true or false depending on whether its input integer is a leap year or not.

A leap year is divisible by 4, but is not otherwise divisible by 100 unless it is also divisible by 400.

* 2001 is a typical common year
* 1996 is a typical leap year
* 1992 is another typical leap year
* 1900 is an atypical common year
* 2000 is an atypical leap year

## Test setup

If we are going to write tests, we are going to need a testing framework. One of the most popular testing frameworks for Java is JUnit. Today we'll use the latest and greatest JUnit 5. JUnit has a built-in assertions library, however it is not great at giving useful feedback for failing tests. Instead, we'll use AssertJ, a fluent assertion library.

To download external libraries into our Java projects we will be making use of a build tool called Gradle. Here's how my gradle file looks right now. Pay special attention to the dependencies and make sure yours match these. Feel free to use Maven if you prefer. Check out any open source JVM libraries at [Maven Central](https://mvnrepository.com/repos/central).

{{< gist SDiamante13 2bfe1c38a50f748e7800e8da2a1a478b >}}

Let's get started by writing a failing test. I like to start new projects like this to make sure everything is set up correctly.

{{< gist SDiamante13 ac587b0a8c9d7af1f610205d5e9dc7f0 >}}

Here we would expect a red bar since true does not equal false.

![alt text](/images/leap-year/assertJFailing.png)

Now let's make it pass!

{{< gist SDiamante13 157105d308aaa06c209119dc2204d15b >}}

Great! Our testing framework is operating correctly.
![alt text](/images/leap-year/assertJPassing.png)

Now that our code is in the green we can refactor a bit before we start with the kata.

Let's begin by statically importing the assertThat method from assertJ. This will reduce the clutter and make our intentions clearer.

Place your cursor on the word assertThat and click option + enter (or alt+enter on WINDOWS). You can also right-click and select *Show Context Actions*. IntelliJ will give you options on how to can better organize the code. 

Select the option saying *Add static import*
![alt text](/images/leap-year/importStatic.png)

Now we can get rid of unused imports by selecting optimize imports
![alt text](/images/leap-year/optimizeImports.png)

Here's the result of that small move
{{< gist SDiamante13 48b0b8bbc2ea332d0071228ef2b3de82 >}}

Let's start by renaming the test method to make it clear about what behavior is under test
{{< gist SDiamante13 fb486702ab12afe4a2d9c325b2cc4a7f >}}

Let's write our first test case! 

A unit test is composed of 3 main parts. Arrange, Act, and Assert. We will be focusing on the Act and Assert for the most part since our simple method does not require much setup.

The Act part consists of calling the system under test. The test plays the part of our method's first caller. When we call the method we want to capture any return variable and compare that with our expectation.

That brings us to the Assert part. This is the true heart of a test case. 

This is where we answer the question: 

Is what I got back from this method what I expected to get back?

We don't need to write tests in any particular order, so we are going to start backwards and start with the end in mind.

![alt text](/images/leap-year/startWithAssertion.png)

So for a common year case we are expected the boolean that comes back our method to be false. 

Since we have called on a variable that does not exist let's bring that variable into existence with power of context actions!
![alt text](/images/leap-year/letIntelliJDoTheWork.png)

Let's assign the *isLeapYear* boolean to the return value from a new method that does not exist yet. We will pass in the year 2001 into the new method as it is not a leap year.  
![alt text](/images/leap-year/act.png)

Now we can create the class that will contain the method under test. Underneath the test fixture declare a new class called Year. Now we can use context actions again to auto-generate the method signature for _isLeapYear_.
![alt text](/images/leap-year/createNewMethod.png)

Instead of returning false like IntelliJ will default to, we should make our test fail first. It's important to see a failing test before making the test pass. This habit will ensure that the tests we write are useful and will catch regressions. 
{{< gist SDiamante13  5c2932ec4dd90abb1308fc8d953e3e60 >}}

Now let's run the tests by clicking the green play button to the left of our test class.
![alt text](/images/leap-year/green-button.png)

The test fails as expected! Get in the habit of reading the expected and actual values. Understand why the test failed.
![alt text](/images/leap-year/failingCommonCase.png)

At this point, we want to get back to green as quick as possible. So we ask ourselves, "What is the simplest thing we can do to make the test pass?"
{{< gist SDiamante13  6a5c74d409e03796db370a8a6d9b1b63>}}

Yes! Just return false. That's the simplest thing!
![alt text](/images/leap-year/green-bar.png)

Now we are back in the green, so we can safely change the structure of the code. Remember to always run your tests after each refactoring move.
Our only move this round will be to address the yellow context action hint asking us to use a different assertion method.
![alt text](/images/leap-year/refactorTestCode.png)

This is how the code looks so far
{{< gist SDiamante13  b0498dc7492d06c3ed8e128565ebb91f>}}

There's not much else to refactor at this point, so we will add another test case. This time we will pass in a year that is a leap year.
{{< gist SDiamante13  9c5d701b7edf69abcbd04458612026b6>}}

As expected the new test fails, because our method is currently returning false for everything.
![alt text](/images/leap-year/leapYearCaseFails.png)

Let's do the simplest thing again and get back to the safety of green.
A simple conditional check on the year is the simplest thing to do right now.
{{< gist SDiamante13  d742e78bc11b2a936f9766258a2bdce3>}}

Let's add another leap year case to force us to use a more general algorithm instead of hard coding the year values.

![alt text](/images/leap-year/anotherLeapYearFails.png)

We are failing momentarily. But we can add to our conditional to get back in the green. If year equals 1996 or 1992 then return true.

{{< gist SDiamante13  f5136131931ad2b2e26ebd4e307a14ae>}}

After the test passes, we can replace the hardcoded values with a proper algorithm. This algorithm follows the original business use case that states that "a leap year is divisible by 4".
{{< gist SDiamante13  29069fbf55050ee931199a5e3cad3300>}}

Our tests are starting to grow quite a bit and have tons of duplication. Although duplication in test code is not as sinful as it is in production code. We want to have tests that are easy to read, understand, and maintain. A great way to reduce this kind of duplication is with a parameterized test.
{{< gist SDiamante13  7ea5c67a02ba5371ef981b84c824baa9>}}

Fully replace existing test cases with parameterized tests.
{{< gist SDiamante13  319889a8b05853d9416f4a5c9fe0e58b>}}

Let's run our new parameterized test. We can clearly see the input and expectations listed. This is much more readable.
![alt text](/images/leap-year/parameterizedTestPassing.png)

We can now remove the unneeded test cases as they are covered with the parameterized test now.
{{< gist SDiamante13  04fca02b70ab00205ae9c3466d548069>}}

Time to write another test case. This time we check the atypical common year case. This is not a leap year, because it is divisible by 100.

{{< gist SDiamante13  8f18656d20d75343c6324f5115568fd0>}}

As expected, the test fails. Let's handle this new requirement.
![alt text](/images/leap-year/atypicalCommonYearFails.png)

We can make the test pass by simply adding another check in our conditional statement. A leap year is divisible by 4, but is not otherwise divisible by 100.
{{< gist SDiamante13  5c5c8b3addaf3991b5d19aed049abfed>}}

Refactor time again! Let's change the parameterized test name to be more accurate.
{{< gist SDiamante13  2d5d477f75958460da4b282ad1e1d5a1>}}

Let's add our last test case. The year 2000 is a leap year because it is divisible by 4 and 400.

{{< gist SDiamante13  2b23618b8eb5542590b4808e848c8eea>}}

This test fails as we are currently not handling this requirement.
![alt text](/images/leap-year/atypicalLeapYearFails.png)

Our code now handles all the cases. A leap year is divisible by 4, but is not otherwise divisible by 100 unless it is also divisible by 400.
{{< gist SDiamante13  465dd611f5cd913d86c84de54691142b>}}

We could definitely stop here. However, since we have our code fully covered by tests we can change the design to improve the readability and future maintainability of the code.

Currently, our code is good, but it could be more readable. What if a junior developer joins our team next week, and they don't understand what the modulus operator does. It's not very clear from reading the code that this does what our business use cases originally stated.

One way to improve code readability is to look for duplication. There is some duplication in checking if a number is divisible by another number. Perhaps, we can extract a method out of this.

First, to allow the IDE to work its magic we will prepare for extracting the method. We want our new method to take in a number that we will check if the year is divisible by that number. To do that, we can introduce variables for 4 and 400. 
{{< gist SDiamante13 e77902afaa410ae846596affd2cfc728 >}}

Select the statement `year % four == 0` and choose the extract method option from the refactoring menu. Choose a name for the new method like isDivisibleBy.
{{< gist SDiamante13 a49a578af8698152a919a0e08e6e67c4 >}}

Next, we can convert isLeapYear to instance method. By doing this we can have year be an instance variable. That way we can have access to it in the isDivisibleBy method. It will make it very easy to read. I'd imagine that Year would hold other properties that are relevant to a year.
{{< gist SDiamante13 787b4e93d473fc17723acda72a5c0c98 >}}

Introduce field and default constructor to safely migrate the year currently being passed in through the instance method to be passed in the constructor instead.
{{< gist SDiamante13 a09482c90d8b07ef3b12ffa72c60a436 >}}

Now pass in the givenYear through the new constructor. Remove the this.year = year line.
{{< gist SDiamante13 449971b3cd59cf8803a1cb316396808a >}}

Safe delete the default constructor as it's no longer being used.
{{< gist SDiamante13 167def399f5d2a509e927249f8db5b39 >}}

Oops! Had to reintroduce the default constructor and then convert isDivisibleBy to an instance method. You can do this manually or by selecting convert to instance method on the refactoring menu while having your cursor on the method name. Now it's safe to remove the default constructor.
{{< gist SDiamante13 ba1d8bcc715019bb960a0d5234f06acc >}}

Use instance variable instead of parameter.
{{< gist SDiamante13 e71c3c9284375987535bf79d86468cff >}}

Now, let's do the same thing for the code checking that the year is not divisible by 100. We can a extract method called isNotDivisibleBy.
{{< gist SDiamante13 764d497f16b803312a9a1e691e8219f4 >}}

Rename parameters of private methods. Move private methods to bottom of file.
{{< gist SDiamante13 2d67894fa1bbbd0dc275c42dd93e70de >}}

Remove parameter year from isLeapYear and instead use the instance variable that the private methods make use of.
{{< gist SDiamante13 5d9d84b3098ea0dc6509406e1e9bc18b >}}

Simplify if else. isLeapYear is now very readable and is at a single level of abstraction.
{{< gist SDiamante13 4fec8b4ac2568ee935b0e42ef77925be >}}

We're just about done. We can move the Year class to the main sourceset.
{{< gist SDiamante13 0fa49b9d155418bfd9ce1bf7b82623c4 >}}

And here's the test code by itself.
{{< gist SDiamante13 cd851cd6fe2bb9844273f959ce61e930 >}}

## Practice!

TDD is not only extremely effective for programming the software you want to build, but it's also fun! The continuous cycle of red-green-refactor is very rewarding. TDD gameifies development for me.

I was fortunate to start my career using TDD. I no longer have to experience the pain of trying to recover my broken software. While doing TDD, my code is always 1 minute off of working. This kind of assurance is very liberating.

Here's a great website I use to find coding katas

> https://kata-log.rocks/