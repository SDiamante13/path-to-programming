---
title: "Testing with Mockito"
date: 2020-01-18T21:19:21-06:00
tags: [testing, mockito, junit]
featured_image: "/images/mockito.jpg"
description: "This is a guide about how to use JUnit and Mockito to write effective unit tests."
draft: false
---

# Why write unit tests?

As developers, we want to write code that works and has as few bugs as possible. For example, when we write some production code we expect that given an input of `abc` the application will respond with `123`. Writing and running automated tests can give developers a high level of confidence that their code does what it's supposed to do. Unit tests isolate the *system under test* and throw a variety of scenarios in the system's direction. Unit tests should be isolated, fast, automated, deterministic, writable, and readable. In this article, we will focus on one of the tools that helps us isolate our tests. Before I dive into Mockito, I must bring up the design pattern of Dependency Injection.

# The Importance of Dependency Injection

Dependency Injection is a way of decoupling objects from their dependencies. Instead of providing a new instance within the class under question we can inject an already instantiated object of the given type into the class. Let me illustrate this using an example. 

Say we had a class named CustomerService which interacts with a CustomerRepository. You could say that the CustomerRepository is a dependency of the CustomerService. Without dependency injection here's how you would set this up.

{{< gist SDiamante13 182b63840b8aa4f47e77fb0da52f06ee >}}

There are a few issues with this approach. First of all, it is memory inefficient. Every time this method is called we are instantiating a new instance of the CustomerRepository. Secondly, it is difficult to properly unit test the CustomerService in this state. We have no way to isolate the system under test. In this state, CustomerRepository will always be tied to this method and is impossible to mock. 

You know you are doing Dependency Injection right when you eliminate the usage of the `new` keyword. So let's do that and apply the Dependency Injection pattern. In the Spring world, there are three ways to inject a dependency. You can use the annotation `@Autowired`, constructor injection, or setter injection. I am going to show the most preferred way which is constructor injection.

{{< gist SDiamante13 55bac9b8d069f636b8b79db16533f3ac >}}

Now... that's better. We can freely pass in any instance of a CustomerRepository to the CustomerService class, even a mocked instance.  There are other aspects of Dependency Injection within the Spring Context that I could touch on such as beans and stereotypes, but I will leave that for you to explore on your own.

# JUnit Refresher

Since this article is more about Mockito I am going to briefly review some JUnit4 basics so we are all on the same page. Let's take a simple example of a calculator and test the behavior.

{{< gist SDiamante13 39db37d48f133e735d8008d3070c26a5 >}}

Now here are some tests that call the methods of the Calculator class and assert the results based on an expectation. For all of the following tests I will be using AssertJ's Assertions library. The import is included in the Spring Boot Test dependency.

{{< gist SDiamante13 8a49910f5328f2eeed6534a74848acab >}}

A popular way of arranging a unit test is by organizing it into three stages: Arrange, Act, & Assert.

The Arrange stage is where you set up your mocks and input data.
The Act stage is where the method under test is called.
The Assert stage is where the result of the method call is compared to the expected value.

# Mockito Basics

Okay now let's dive into Mockito and mock some of our dependencies so that we can properly unit test the system under test.

I will continue with the CustomerService example from above.

I will show two different ways to mock objects with Mockito.

{{< gist SDiamante13 12650f2ebc9e9a11e0dfc37255d0355d >}}

The first way is to use an annotation runner called `MockitoJUnitRunner`. The annotation `@Mock` declares your variable as a Mockito mock and the annotation `@InjectMocks` will inject all dependencies into the class under test.

{{< gist SDiamante13 143a235c0b273ac24996683f4f90156e >}}

The second way is done without annotations. Both ways are appropriate and achieve the same result. It is based solely on personal preference.

## What is a Mock?

Mock is a confusing term, because often times it is used to describe multiple things. There are different objects you can build to facilitate unit testing. You could use a test double, a spy, a mock, or a stub. In this sense, a Mockito mock takes the shape of a test double, but I will refer to it as just a mock. A mock is a fake object that has the same methods as the real class, but the methods do not have any actual code inside of them. All mocks return null (or 0 in the case of primitives) unless specified to return something. So now let's make our mock return something.

{{< gist SDiamante13 2607e721351a1b23f0b08a418c93556d >}}

You can see that Mockito is easy to read and understand. **When** this **mock object** calls this **method** then **return this value**. So in the act phase we call the method and that in turn calls our mock which we have provided its output. 

## Why should we use mocks?

We use a mock because we have already tested that the CustomerRepository does what it's supposed to do. We shouldn't let its behavior interfere in the CustomerServiceTest so we will control its behavior instead.

## Verify a method was called

Sometimes we are satisfied with a test that verifies that some method is being executed. For that we can use Mockito's `verify` method. 

{{< gist SDiamante13 06b51ff0193927b54d06c655e75e9124 >}}

In this test we are saving a customer to the database. Instead of using an assertion, we are going to use `verify` to ensure that we have saved the customer we said we would. The `times` property is optional in this case since the default is 1 time, but if we were calling this method multiple times we could make sure we always call it that many times given the circumstances.

## BDDMockito

In the Mockito library there is another set of methods that offer the same features, but with a slightly different syntax. BDD stands for Behavioral Driven Development. BDD follows the `given` `when` `then` pattern of acceptance criteria. Much like Test Driven Development, BDD starts with a failing test and then code is written to make that test pass. So using the same examples as before I am going to demonstrate how you would write a BDD style test using BDDMockito.

{{< gist SDiamante13 f8cf75cbb9587c16781e43bbf49b12a7 >}}

Some people prefer this way since it is easier to read and understand. Now I will show you what the verify equivalent would look like in BDDMockito.

{{< gist SDiamante13 f2224ec7300e524a835fd8bc7b747ad1 >}}

# Advanced Mockito methods

Now that we have covered the basics let's move on to some more advanced topics.

## Spy

A spy is a partial mock. It is a wrapper around a real object. All of a spy's method calls are the real thing, however at any time you can stub the spy's method responses and verify method calls.

Here are the two ways of declaring a spy using Mockito.

{{< gist SDiamante13 8725c4b01f3318e3bede508a3bc60d18 >}}

One tricky thing about stubbing the method call of a spy is the change in syntax.

{{< gist SDiamante13 391e3271c88e99ea2620021ca8af13cf >}}

When stubbing the method of a spy you must use the doReturn & when methods. The reasoning for this is that a spy can call real methods at anytime so we must be careful. If you were to write `when(spyCustomerRepository.findById).thenReturn(customer)` that would actually execute the findById method. Since doReturn places the method on the outside of the parentheses, the method will not be called before stubbing it. 

## Argument Captor

Argument captors can be a very useful tool in the right situations. When verifying that a mock's method was called you can capture the value that was passed in and perform assertions on it.

A good use case for argument captor that I recently discovered is while testing that an entity has been saved. Most database tables use a timestamp column for their entities. If you just used verify by itself, then the expected and actual timestamps could be a second off due to the lag of the unit test. 

{{< gist SDiamante13 1d6fda6f8ed76cdb6e8b26be732e8b0d >}}

Time delay is something we never want to introduce in our tests. This can cause the test to be flaky. A flaky test is a test that fails sometimes even without changing any code. 

To avoid this you can capture the actual object that was saved and compare the two customers while ignoring the timestamp value.

## Answer

For most test cases, a simple stubbing of a method is sufficient enough. However, sometimes we need a more advanced technique to deal with complex methods. The Answer method can be used to retrieve the inputs to a method and alter them. This works great when dealing with void methods that manipulate the input.

The test below is testing the behavior of saving a customer in a PostgreSQL database. The Customer entity has an autogenerated id using the `javax.persistence @GeneratedValue` annotation. When we save the customer without an id and the database will automatically assign it an id. To mimic this behavior in a test scenario we can make use of the Answer method. We can retrieve the Customer object that has been passed to the save method and set its id field.

{{< gist SDiamante13 ba890a8eb10829056d91942ff6befb20 >}}

Other use cases for using Answer are for void methods and asynchronous calls.

This is an example of a class which uses an asynchronous Runnable method that will sleep for 3 seconds and then return a string.

{{< gist SDiamante13 5c41a4fd01b878a9afedc91fb4ba00c8 >}}

If we were writing a test for the method `getData` we would have no way of stubbing the Client class with the when & thenReturn methods since the method `processData` returns nothing. The test above fails due to the client being a mock and we have not set up any action for the mock to do. This is a simple example, but it shows the need for using Answer.

{{< gist SDiamante13 97af9533ec9af9620ceff5774e0124b6 >}}

In the example below, using Answer we can hijack the Runnable passed to the `processData` method and run it. This executes the sleep and returns the correct data.

{{< gist SDiamante13 e7ce7d4c8f1d0970f43b9454cbeadc13 >}}

## InOrder

When verifying that specific methods are called we may want to ensure that they were called in a specific order. We can use `InOrder` to verify the order. 

{{< gist SDiamante13 d941bb61d8d2dd5324bd1aa6f6dbafa0 >}}

Without using InOrder this test would pass, however since `findById` must be called first we receive this error.

    org.mockito.exceptions.verification.VerificationInOrderFailure: 
    Verification in order failure
    Wanted but not invoked:
    customerRepository.findById(1L);
    -> at com.diamante.orderingsystem.service.customer.CustomerServiceTest.
    updateCustomer_findsTheCustomerById_andUpdatesTheCustomerInTheDatabase
    (CustomerServiceTest.java:67)
    Wanted anywhere AFTER following interaction:
    customerRepository.save(
    Customer(customerId=1, firstName=Sam, lastName=Adams, paymentInfo=
    PaymentInfo(cardNumber=4372762, expirationDate=7/12, 
    securityCode=345, zipCode=87262)));
    -> at com.diamante.orderingsystem.service.customer.CustomerServiceImpl
    .updateCustomer(CustomerServiceImpl.java:54)

So when the order of the methods being called matter in your test consider using InOrder.

# Conclusion 

So we've covered a lot in this article. We've seen how to declare mocks and stub their associated methods. We've seen examples of using Spy, ArgumentCaptor, Answer, and InOrder. Each have their own place in unit testing. Knowing how to set up and stub a method comes with practice. So go forth and write unit tests for your code so that you can be confident that it does what you expect it to do. 





