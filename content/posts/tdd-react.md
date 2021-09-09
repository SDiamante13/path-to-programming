---
title: 'Experiencing the behavior driven design of using TDD with React Testing Library'
date: 2021-09-09T17:00:00-00:00
tags: [jest, react, testing, XP]
featured_image: '/images/tdd-react.png'
description: 'This is a reflection on my practice of blind coding a website using TDD'
draft: false
---

# TDD in React

Test driven development (TDD) is a tool for breaking down complex problems into more manageable chunks. This post will explore my journey of applying a TDD approach to website development using React, {{< a_blank title="Jest" url="https://jestjs.io/" >}}, and the React Testing Library. In this experiment, I didn't look at the browser for feedback at all. Instead I got all of my feedback from the automated tests. By focusing on the behavior of the components I'm building, I am able to get a working UI quickly and I'm able to change it's behavior while still verifying its accuracy. Also, I ignore all of the styling until I am happy with the behavior of the system.

# The XP Way

When I started programming professionally, I learned it in an XP way. For more info on Extreme Programming check out my article on [XP compared to Scrum]({{< ref "xp-scrum-compared-pt1.md#engineering-practices" >}} "XP compared to Scrum.") My career has always been more than a job. Any product I find myself on, I care deeply about the code, design, architecture, and prosperity of the product.

One practice I learned and still continue to, was how to build software through the usage of TDD. Most people have the misconception that TDD is about enforcing tests in our code. But as you will see, it is much more than that.

# Why does TDD work?

It is human nature to want to break down large problems into smaller problems. By focusing on the behavior you would like to create you step away from the larger problem at hand. Nowadays, there are many talented developers that are creating life changing software. The breadth and depth that our software products have is immense. By using TDD as a tool, we are about to break these gigantic problems into one question? What is the simplest thing I can do to make this test pass? We use tests to dream up a behavior that we wish our software would do. And then that dream becomes a reality. Some people call it {{< span style="color:red;" text="red" >}}, {{< span style="color:green;" text="green" >}}, {{< span style="color:blue;" text="refactor" >}}, but you could just as well call it {{< span style="color:red;" text="dream" >}}, {{< span style="color:green;" text="reality" >}}, {{< span style="color:blue;" text="optimize" >}}.

# Attempting TDD on Android

When I was on an Android mobile app team early on in my career, I wasn't able to apply TDD enough on the app. Something about having the UI there always distracted me. I would lose that flow that us TDD practitioners love to be in. Too much context switching or long running phases of red will break this flow. On my team, we would always style, design, and add business logic all at the same time. It was way too much all at once. Over time I've learned to break down those different parts of the design process.

We weren't using testing libraries that check for the behavior of the UI. Although, we did have some {{< a_blank title="Espresso UI" url="https://developer.android.com/training/testing/espresso/" >}} tests that are much like the {{< a_blank title="React Testing Library" url="https://testing-library.com/docs/react-testing-library/intro/" >}}, those were not a part of our everyday local development. For these reasons, our team, which was actively applying XP practices to a mobile product, was not able to achieve a high level of TDD compared to the backend teams in the portfolio.

# Attempting TDD on React

Recently I have been using TDD to generate websites using React and the React Testing Library. Instead of having a browser window open to view my changes, I just execute `npm run test:watch` which executes `jest test --watch`. Now, I have a quick feedback loop! And most importantly, LESS CONTEXT SWITCHING! I can dream up some magically behavior I want my UI to do and I can let my automated tests drive towards an optimal design. Most newcomers to the practice don't really understand that at the root of TDD it's all about design. By taking small steps, we only leave the danger zone for short amounts of times. The danger zone being that uncomfortable amount of time where your tests say that your dream and your reality are not aligned. Your software does not work the way you expect it to.

## Let's break down my thought process

1. I want to add new behavior to my website
2. This is my criteria for what will happen when 'x' happens
3. DANGER! The software is not in a working state
4. Do the simplest possible thing to get back to safety

## Jest test case

Here's a test case I wrote for a task manager application:

```javascript
it('should add new tasks when enter key is pressed', async () => {
	renderComponent();

	addNewTask('Take out the trash');
	addNewTask('Write Blog Post');

	screen.getByLabelText(/Take out the trash/i);
	screen.getByLabelText(/Write Blog Post/i);
});
```

And here are my helper methods so you understand what methods I'm using from the React Testing Library:

```javascript
const addNewTask = (taskName) => {
	const taskInputField = getTaskInputField();
	type(taskInputField, taskName);
	pressEnter(taskInputField);
};

const getTaskInputField = () => {
	return screen.getByRole('textbox', { name: /Add New Task/i });
};

const type = (input, text) => {
	fireEvent.change(input, { target: { value: text } });
};

const pressEnter = (domElement) => {
	fireEvent.keyPress(domElement, { key: 'Enter', keyCode: 13 });
};
```

As a user I want to add a task and I can accomplish that by typing my task into the input field and clicking the enter button. This test has that same behavior baked into it. After I wrote this test case I wrote the code necessary to make that happen.

Here's a small snippet of the JSX for the Task Manager:

```javascript
return (
	<div>
		<h1>Task Manager</h1>

		<div>
			<label htmlFor="task">Add New Task</label>
			<input
				id="task"
				name="task"
				type="text"
				value={task.name}
				onChange={handleChangeEvent}
				onKeyPress={handleKeyEvent}
			/>
		</div>
		<TaskList tasks={tasks} onCompleted={handleCheckBoxEvent} />
	</div>
);
```

# Programming is fun with TDD

For me, TDD gameifies programming. I love playing games and when I'm enforcing the practice of TDD it makes it feel like I'm playing a game. It makes programming fun!

# Distracted by UI

One reason why I wanted to try this was due to a problem I've been having lately. While working on building a website I am often getting distracted by wanting to style my content before I've even programmed the behavior of it. I'll always have a thought like "oh I want this part to be blue... and now let's make this App Bar perfect!" But hey hey wait, all of that stuff can wait!

So I stop and ask myself...

What is it that the user of this product wants it to do?
How can my website achieve that behavior?

This is where TDD in React really shines. By leaving the styling towards the end, we have guaranteed that the application works like we expect it to work. And now we can focus on all of the details of the UI, UX, and A11y, In my opinion, adding styling is more like visual refactoring. The definition of refactoring is restructuring the code to work in a better way without modifying the current behavior of the system. By adding styling to the components last, we are just restructuring the layout of the components that have already proved themselves to exhibit the behaviors we have designed for them. We are giving them color, depth, and space to harmonize amongst the other widgets, text, and buttons on the screen.

After exploring TDD in React I discovered an even better way to do it.

Outside-In TDD.

Maybe next time!
