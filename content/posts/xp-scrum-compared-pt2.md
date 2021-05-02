---
title: "Agile Methodologies: Comparing XP and Scrum Part 2"
date: 2021-05-01T22:25:31-05:00
tags: [agile, soft skills]
featured_image: "/images/agile_cover.png"
toc: true
description: "This post is part two of a two part series which explores the similarities and differences between Scrum and XP. I also share my own experiences on transitioning from XP to Scrum."
draft: false
---

## XP and Scrum Differences

This is a continuation on where we left off in the previous post: [Agile Methodologies: Comparing XP and Scrum]({{< ref "/posts/xp-scrum-compared-pt1" >}} "Comparing XP and Scrum Part 1"). Last time we discussed the origins of Agile and began to explore some of the differences between XP and Scrum (i.e. sprint cycles and engineering practices). Let's get back into it!

### Code Reviews

A code review is a process of letting a person other than the original code developer inspect the new code changes. In Scrum, code reviews are often a requirement to ship a feature to production. Common things that reviewers look for during a code review are coding style, defects, performance concerns, adequate test coverage, and good coding patterns.

Due to pair programming, XP teams rarely engage in formal code reviews. Pair programming is viewed as a ongoing peer review process. I've been on a team that combined pair programming and code reviews. Our team felt that this extra precaution would help reduce defects that we were frequently experiencing after deployments. This is a rare case and most people would say that the pair programming practices should have been improved, but whatever is best for the team is best. This was my only experience with code reviews before coming to the Scrum world&mdash;I still have a lot to learn on the subject.

### Team Rotations

In my two and a half years of working in an XP environment, I was on six different teams. Every month we would rotate a few people around the different product teams. I love the idea of this and it solves a lot of issues, but it must be done with care. Due to the development team pair programming daily, the business context was fairly distributed throughout the team, so losing a developer to another team and getting a new one in return was not a big deal.

Team rotations help with spreading context around to other teams. It can bring fresh new perspectives to a team. I've seen developers switch teams and bring patterns and tools that they were using on previous teams to help improve the processes of their new team. I like the chance to work with new people, different technology, and solve different problems. I'm a huge advocate for team rotations and would encourage all product teams to give it a try regardless of your Agile methodology.

### Team Roles

The product team roles in XP and Scrum vary in title, but overall they cover the same breadth of responsibilities.

![Product Team Roles](/images/team-roles.png)

##### Scrum Master

The Scrum Master's role is to improve the team's effectiveness and practices within the Scrum framework. Scrum Masters can help developers get unblocked by getting them in contact with the right SMEs. They pay attention to delivery metrics and strive to improve the efficiency and throughput of the product team.

XP teams do not have roles called Scrum Master. Instead, through pairing and open discussion they hold each other accountable to participate in the necessary rituals and meetings to be successful as a collaborative team. Any other responsibilities are taken on by the product manager.

##### Product Owner

The product owner (or product manager in XP) is responsible for maintaining and promoting the product vision. Their duties include, but are not limited to, managing the product backlog, talking to stakeholders about the future deliverables of the product, and setting the priorities for the product.

##### Cross functional team members

The rest of the team is composed of developers, designers, architects, analysts, and DevOps engineers. On my XP teams, we had less roles than what I've seen in Scrum. Usually this will lead to the developers taking on more tasks outside of just development work (i.e. DevOps, architecture).

My current team has a technical lead on it. This person participates in many meetings with stakeholders and other teams. They also lead technical discussions, perform code reviews, and share context with the other team members. On my XP teams, we called this role "The Anchor". The roles were similar, but many teams I was on encouraged taking turns with attending business meetings as to not have one person end up with all of the context.

## Similarities between XP and Scrum

While they have their differences, XP and Scrum are both Agile frameworks so they share a lot in common as well. Things you may see in both frameworks are daily stand up, retrospectives, iterative planning, user stories, story point estimation, customer feedback, cross functional teams, and product road maps.

### Similar Agile Ceremonies

There are some regularly occurring meetings that guide the team through the Agile process. All of these meetings can be seen in XP and Scrum, however they may have different names.

![Agile Ceremonies](/images/agile-meetings.jpg)

##### Daily Stand Up

The Daily Stand Up meeting is a staple of most Agile teams. The main purpose of this meeting is for teams to start their day together and give updates on their work in progress. The name "stand up" comes from the fact that this meeting should be conducted with all team members standing up. This is a way to keep these meetings brief and to the point.

Each team member will take turns answering three general questions:

> What did you do yesterday?

> What will you do today?

> Do you have any blockers on any of your tasks?

##### Sprint Planning (Iterative Planning Meeting)

Both Scrum and XP have a meeting where the product owner will go through and prioritize the work in the backlog. The user stories reviewed in this meeting are explained, clarified, and eventually pointed by the team. Most teams I have been on use a Fibonacci pointing system. The possibilities are: 1, 2, 3, 5, and 8. The more points a user story is, then the more complex it is in terms of effort and scope. Pointing stories allows teams to establish a velocity so they can have a better understanding of the pace at which they get work done. This metric helps with estimating work in the future.

##### Sprint Review (Demos)

The Sprint Review is crucial to the Agile process as it's an opportunity for product teams to show off what improvements they have made to their products. This is a great meeting to receive feedback and see what other teams are working on.

##### Retrospective

The retrospective meeting occurs at the end of the sprint. This meeting is a chance for the team to connect, grow, and improve. There are many different formats of how this meeting can be ran, but the main goal is to figure out what went well and what went not so well. The good items are opportunities for team members to appreciate each other's hard work. The not so well items are opportunities for the team to improve in the future. Generally these items can drive action items that individuals can follow up on for the next sprint. Retrospectives are one of the most important meetings for improving the Agile processes and efficiency of a team.

## Why isn't XP more popular?

According to the latest [State of Agile Report](https://explore.digital.ai/state-of-agile/14th-annual-state-of-agile-report), 1% of all respondents use XP, while 56% of respondents use Scrum. So, why aren't more organizations adopting Extreme Programming?

![Agile Method and Practices](/images/agile-methodologies-used.PNG)

I think the answer has a lot to do with the strict Engineering practices that XP requires from the development team. If you're an organization transitioning from Waterfall to Agile, then it will most likely take less time to transition to Scrum than XP. If we analyze the two big requirements XP asks its practitioners to do, it makes sense why. 

At surface level, pair programming seems like it's splitting a team's throughput in half. I understand that view point since that's how I thought of it at first too. But upon closer look we can see that **over time** pair programming eliminates the need for code reviews, reduces defects, increases developer morale, and helps spread good design principles that in turn reduce technical debt.

Test driven development is seen as unimportant since tests are not production code so it's slowing down the rate at which a team can release software. Generally speaking, managers don't care about code quality or tech debt. TDD and refactoring can help developers to be able to change code more easily. Developing the skill and reflect needed to perform TDD at a high level is quite an investment in itself. It's not intuitive and most teams settle for writing their tests afterwards or sadly none at all.

The benefits of exercising pair programming and TDD are not immediate. It can take time for development teams to get used to these practices and excel at a high level. However, by eliminating technical debt along the way and having good developer practices your product will endure the changing landscape of the software industry.

On the report discussed above, 8% of respondents use a Scrum XP hybrid approach. I think that the structured nature of Scrum combined with the sustainability and sound practices of XP makes for a great pairing.

## Conclusion

Whether your team uses Scrum, XP, or some other methodology you should never be afraid to experiment with different ways of working. Most of these frameworks are flexible and that is evident by the different ways they are implemented across organizations. At the end of the day, Scrum and XP are both Agile and their purpose is to produce high quality software for their customers.

## Find me on Twitter and let's chat!

> What Agile methodology are you currently utilizing? 

> What are some of your favorite Agile ceremonies and practices?


Tweet me at @SDiamante13 with your answers!

## Resources

- [Extreme Programming Explained](https://www.amazon.com/Extreme-Programming-Explained-Embrace-Change/dp/0321278658)

- [The Scrum Guide](https://scrumguides.org/scrum-guide.html)
