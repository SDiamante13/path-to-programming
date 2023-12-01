---
title: 'How I got my First Software Developer Job'
date: 2021-09-23T10:13:03-04:00
tags: [career, soft skills]
featured_image: '/images/first-job-cover.jpg'
description: 'An account of the process I went through in transitioning from a career as an electrical engineer to being a software developer'
toc: true
draft: false
canonicalUrl: 'https://www.pathtoprogramming.com/posts/first-job/'
---

# How it all started

Today I'm going to talk about how I got into software development. I will be covering my previous career, my move to Chicago, and the interview process that led to my first job in the software industry.

## Life as a Patent Classifier

After graduating from college with a degree in Electrical Engineering, I began working for a company contracted with the US Patent Office. My job was to read patents and place tags on them which would help categorize/classify them. With the patent classified, we would be able to send it to the right patent clerk to be judged for novelty.

### Stuck in a boring job where every day is the same

The job was exciting at first, but it got old quick. I had a daily quota of patents I needed to classify. It required a lot of reading and googling for prior art. I specialized in non-linear circuitry, semiconductors, and amplifiers. Every day was the same and I grew bored of my job. I was lacking challenges and growth in my professional life.

### Learning at the office

I had a lot of free time on my hands at the office so I would often watch Netflix, YouTube, and play games on my phone. After learning a lot about the stock market and investing, I got inspired by my future brother-in-law to give programming another try. He had recently graduated from college and was learning Java. It reminded me of how I always wanted to take a Java class in college. I started learning it right away and got hooked instantly! My first big project was a stock portfolio desktop application that I built using Java Swing. I already had a solid foundation of object oriented programming from my programming courses in C++ at Virginia Tech, so I was learning more and more about how to build applications.

# The Move to Chicago

Eventually after three years as a patent classifier, the company I worked for started to let people go and I was one of them. Luckily my family was already planning to move to Chicago as my wife was going to be starting a new job there. With this life altering decision, it was finally time for me to make a career change and become a software developer.

## The Job Search Begins

When I arrived in Chicago, every day I would go to the local library and apply to many jobs. I would also work on any interview assignments, programming tutorials, or pet projects. That was my full-time job at the time. I would spend 6-8 hours at the library every weekday and rest on the weekends.

## Big City, Big Lights Meetup, First time in city

On just my third day in Chicago, I attended a Meetup event in the city for the {{< a_blank title="Illinois Java Users Group (IJUG)" url="https://twitter.com/IllinoisJUG/" >}}. This was my first time going downtown and I still remember it like it was yesterday. The busy streets, the tall beautiful buildings, and the people walking fast down the sidewalks&mdash;all of it inspired me. I proudly arrived to the 57-story building of HCSC.

### Bruno Souza speaking at HCSC

The speaker for that evening was Bruno Souza. He is a Java Champion and helps developers improve in their career.

![Meetup at HCSC](/images/meetup-hcsc.jpg)

His main highlights come from notes I took that evening:

- deliberate practice - 1 hr deep and wide
- keep reading code, writing code, delivering code
- share what you know
- join a community
- go big

The most important point he made of the night was a single statement:

> I help [people] to do [this] so that they can have [that].

Fill in the [blanks] with what is applicable for your goals.

Follow him on Twitter - {{< a_blank title="@brjavaman" url="https://twitter.com/brjavaman" >}}

### Chatting with employees

An HCSC manager started the night off by announcing that they were hiring. They asked anyone interested to find a employee and chat with them about it.

So that's what I did. After the presentation was over, I talked with an employee and asked him about where I should apply.

### Applying for the job

When I applied for the job the following day I wasn't exactly sure which role to apply for. One of the first roles I saw that had the word developer in it was for the role of "XP Developer". I had no idea what XP meant, but it said something about Java so I went for it!

## The interview process

The job description of the role that I applied for was very intimidating to me. I wasn't familiar with a lot of the terminology. It said things like CI/CD, TDD, XP, PCF, and pair programming. I had to look up most of the words in the description. I learned about them, but without actual practice they were still very unfamiliar to me.

### The phone call

A few weeks later, I got a call from a hiring manager to talk more about my experience and the role I applied for. He said that it was okay that I didn't have much experience in what the position required because I would be able to learn on the job. He also said that the team I would be working on have been hiring several developers from boot camps and other non-technical backgrounds. A willingness to learn and adapt are the qualities they most value.

I wasn't very confident about how the phone call had went. Honestly, I didn't expect to hear back from them at all. But to my surprise, I received an email from the hiring manager with details on the next stage of the interview process. The on-site pairing exercise.

### Implement a Stack

I walked into the office of HCSC and met Heather, a senior developer. She told me that today we would be pair programming together. I informed her that this was my first time pair programming.

"That's okay" she said. "I'll explain along the way. Today you will be the driver. I will be here to answer any questions and guide you along in the process. We will be implementing a stack. You can't use any data structures to implement it. Only basic arrays."

I did fairly well in the interview. I did get stuck a few times, but by the end we were able to use TDD to incrementally get to the final solution. The exercise took about an hour. I returned home and waited for the next steps.

### The all day interview

It took around four weeks to here back from anyone. Finally an email came one day with more information on the final stage of the interview process. The final stage was an all day in-person interview.

I attended the morning standup and introduced myself. Afterwards, as all of the teams were doing their standups, I was able to participate in that as well.

Over the course of the day, I paired with three different developers on three different teams.

### Keeping it Simple

First, I paired with Adam. He was initially intending to work with me on a story regarding RabbitMQ (a messaging broker). However based on my unfamiliarity with it, he decided to keep things simple. We ended up implementing a simple API. It was a contrived example, but the point was to see how I went about solving problems. I had some experience with the Spring framework, but I didn't have much practice with Spring Boot. Also anything other than a very simple unit test was confusing to me. He guided me through it and eventually the 2 hours were up and it was time to move on to the next pairing session.

### Think Before you Code

Next, I paired with Myles. For the first hour, we were getting to know each other and he was explaining the domain of his team. I started to understand the work that needed to be done. We wrote pseudo-code together to put our approach out into the world.

The second hour we finally jumped into the IDE. The project was many APIs, mostly written in Kotlin. He explained the syntax of Kotlin to me and asked me to drive. I was coding in Kotlin for the first time! It was fun and different. We never ended up finishing the implementation, but I thought the collaboration went very well.

### Hunting for a Bug

In the final pairing session of the day, I paired with Tracy. We attempted to find a mysterious bug in the Member API that was reported by QA. I was pretty confused on how to find where this bug was occurring. After a long day, I was worn out and needed a lot of assistance for this one. I don't think we ever ended up fixing it. Luckily for them, it was a scenario that already occurred weeks ago. She was just using it as an example for the interview.

### Reflection on the interview

Overall that was the most interesting interview I've ever had. It really helped me get a sense of what a typical day would be if I got the job there. I was able to meet and work with the other developers&mdash;I felt like I was a part of the team. I didn't have to answer questions like "What is your biggest weakness?" or "Where do you see yourself in five years?". Instead, they got to see how I would perform on the job and I was able to experience what it would be like working there.

## We are the champions!

Three weeks later, I received a call from an HR rep at HCSC.

> I got the job!

I was so excited and keeping most of it inside. We discussed some details and next steps, finally saying our goodbyes.

I immediately grabbed my phone and searched for the song "We are the Champions" by Queen. I played that song at least three times and was dancing around my room, filled with joy.

I had come to Chicago unemployed with a four-month-old daughter and had recently purchased a house. I put in so much effort trying to start my software developer career. I applied to over 200 jobs in a span of two months. My hard work had finally paid off. Finally, a company saw the potential I saw in myself.

## One Developer's Journey

So there it is. That is my journey from patent classifier to software developer. I am truly blessed to love what I do for a living.

If you are currently in a similar position that I was in

- Keep your head up
- Always believe in yourself
- Strive to learn some new technical knowledge everyday
- Attend meetups
- Find a mentor and learn from them
- Never give up&mdash;you've got this!

Thanks for reading! If you want to share your own journey with me please feel free to contact me through Twitter, LinkedIn, or through the comments below!
