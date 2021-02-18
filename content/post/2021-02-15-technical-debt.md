{
"title": "Techical Debt",
"date": "2021-02-15"
}

Technical debt is defined as _“…the implied cost of additional rework caused by choosing an ill-suited solution —could be easy, limited or over-engineered— now as opposed to using an appropriate solution.”_ [1]

It is the effort that builds up when a team makes a conscious decision to implement code that’s regarded as a quick fix, instead of building out the best solution. The _quick fix_ is the “debt” and like any kind of debt, it accrues interest over time, so the additional effort built up which could be time, money or resources is the tech debt that builds up and makes it harder to easily implement a better solution. Tech debt is not bad and it is unavoidable; time to market pressure amongst others is what makes tech debt unavoidable, that is if the team doesn’t plan on being in development hell forever 🌝.

# Where Does Technical Debt Come From?

All these incur technical debt because they harm productivity. Some can be directly influenced by the engineering team, others can be influenced by the management.

1. Bad architecture

2. Inconsistent project structure

3. Code duplication

4. Low test coverage

5. Poor code documentation (or a complete lack of documentation)

6. Potential bugs not fixed on time

7. Unnecessarily complex code (over-engineered code)

8. Code smells

9. Scope creep

10. Lack of a QA process

11. Inconsistent deadlines

12. CTO who thinks they’re a god 👀

# Are there other types of debt?

Not all software projects issues are as a result of Technical Debt, so we may ask ourselves, are there other types of debt? These are a few types of debt which are faced by teams around the world.

- **Quality Debt**: is caused by identified defects in the software built.

- **Process Debt**: is caused by a lack of team processes or poorly implemented processes.
- **Feature Debt**: is caused by a team releasing useless or delayed features. It can also be caused by releasing incomplete features with hope to go back and finish and never going back.
- **User Experience Debt**: is caused by inconsistent or poor user experience which has to be redone later.
- **Skill Debt**: is caused by a lack of skills which are required by the team.

# Categorization

How is debt accrued you ask? Well, tech debt can be introduced into software projects in several ways. These three types of debt:

1. **Deliberate technical debt** can be described as intentional choices (i.e., shortcuts) made to deliver on time.

2. **Unintentional technical debt** can be described as an accumulation of debt over time as a result of things like ignored coding standards and practices, outdated technical design, or debt incurred from constant rework and ad-hoc features added to legacy code.

3. **Unavoidable technical debt** can be are caused by factors out of the control of the development team. A third-party system upgrade can force the team to rework some part of the system. Or a language’s/library’s version becomes outdated making the dependent code vulnerable to attacks. Systems or tools that the software depends will evolve and can negatively impact your software.

# Scenarios

1. Say you have an API with an endpoint that takes 1000ms to return a response. Clients consuming that endpoint may wait over a 1500ms —due to reduced network speeds— to receive a response from the server. If you refactor the database queries or introduce a cache layer, we can bring the round trip time (RTT) to 500ms. If you choose to leave it, the performance will degrade over time and the RTTs for that resource will only get worse as the database grows or modifications are made to that resource. This is an example where technical debt is incurred because of the platform architecture.

2. Say you worked on a large part of a large codebase and didn’t write any tests because you had to continue meeting deadlines —I know you wanted to write tests but you just couldn’t. This is not your fault, as the business doesn’t see writing tests as important because it doesn’t directly impact the end-user; their words, not mine 🤷🏿‍♀️. After a few years, you get another gig and move to a new company. Now Raymond, oh poor Raymond; “the new guy”, has inherited the codebase. Before her can make changes to the codebase, he has to go through a lot your code to understand your thought process. To get new features out, he has to understand that neatly nested ternary that made you feel smart or that map-reduce that felt satisfying to pull off. The additional time it will take Raymond to understand and refactor the codebase would have been significantly reduced if you had written the tests originally like you intended to. Similarly, if you have been allowed to refactor that part of the project earlier, it would have made it easier to modify now. Some Raymond’s would duly inform management that a rewrite would be a better alternative than managing the current mess. This is a very common case that almost all the devs I know have experienced and it always ends with tech debt being accumulated.

There are a ton of other examples of how tech debt can be accrued, if I were to list them out I don’t think I’d ever stop typing 😭.

# My experience

In 2019 when my team built the first version of gomoney, we handled certain account properties as a single number; from the account balance to the account’s transfer limits. It was an easy, albeit naive implementation which later came back to haunt us because we eventually built a lot of systems around those two main account properties. Over time the business needed to have specific limits for different kinds of transactions and this posed a problem as the current implementation only supported one limit per account. The ensuing refactor affected about 49 files. That’s a considerable surface area of a project of its size, other parts of the platform were not affected as we’d gone ahead to ensure proper separation of concerns.

![Code](/images/git-image.png)

In my six years as a developer, I’ve had to refactor legacy codebases, rebuild parts of or entire systems, either because the original author of the code didn’t use descriptive variable names, didn’t architect a robust solution or over-engineered the solution. As I’ve heard and read over the years “Your code will be read more times than it’ll be written” [4], so in the bid to get that new feature out, be intentional about how much debt you want to take on and put things in place ahead of time so when you or someone else wants to pay it back, it won’t be a hassle.

# Technical Debt Is Like Tetris

Eric Higgins describes it perfectly, “PMs work with software developers to prioritize features will be built and released to customers next. Finishing a Tetris row is like shipping a feature. Shipping complex features require more rows. The software requires time more time to build correctly and tradeoffs are always made due to business requirements. The tradeoffs are represented by the “spaces” between bricks in Tetris. All code has technical debt. That’s normal and we can keep playing Tetris with a few gaps.” [2]

In our case, we paid our debt when we saw it fit to pay it back, and not before. Doing that would have been premature optimization; premature optimization is not fun at all, because you’ll be optimizing for scenarios that haven’t happened yet, based on assumptions, not experience or fact. I have a personal rule, “first make it work, then make it robust”. I urge you to not try to be a perfectionist, be like a multi-pass compiler, don’t optimise on the first pass, that’s what other passes are for 🙃😌.

# Prioritization

This is a source of great tension between product management and software development teams.
- Product managers often have to prioritize features over addressing technical debt because new features for customers have the potential to generate revenue.

- In contrast, software developers recognize that they could more quickly deliver high-quality features and functionality if they could remove/reduce the technical debt, which impacts the stability and the performance of the software as it accumulates.

I mentioned tech debt categories earlier, however, the categorization does not help with prioritization. Categorizing technical debt using customer impact as the clincher gives the product and development teams a basis for prioritization. The team’s focus should be placed on paying back the technical debt that impacts performance and security which is usually on par with building out new features and functionality.

In this way, we make sure that there’s no reduction in user experience due to a slow, unresponsive or buggy application or platform. It also ensures that we respect data privacy and protection of the customer’s sensitive data by addressing potential security issues.

# Solutions

The team at the Agile Alliance detailed a few ways to tackle technical debt [3].
1. Include technical debt consideration in iteration-level activities — build tech debt into the team’s per-sprint roadmap

2. Factor technical debt into release-level activities —build tech debt into the product’s roadmap.

3. Factor technical debt when implementing user stories — whenever possible developers on the team should pay back technical debt.

# Conclusion

This isn’t a fairytale, and there are no happy endings. Paying down technical debt does not always end in more users and more profit for the business but it’s essential. You can have well-architected code with 100% test coverage, but you may have no reasonable revenue. On the flip side, your company could be one large script running some messy code that makes you a ton of money. Everyone on the team — from management to developers — should share an understanding of what technical debt is. They should know when to acquire tech debt and when to pay it back.


# Citations & References
[1] [Wikipedia definition for Technical Debt](https://en.wikipedia.org/wiki/Technical_debt)

[2] [Technical Debt Is Like Tetris](https://medium.com/@erichiggins/technical-debt-is-like-tetris-168f64d8b700)

[3] [Project Management and Technical Debt](https://www.agilealliance.org/project-management-and-technical-debt/)

[4] [Robert C. Martin Quote](https://www.goodreads.com/quotes/835238-indeed-the-ratio-of-time-spent-reading-versus-writing-is)