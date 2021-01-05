---
title: '400% Over Capacity: Stories From An ETL Engineering Team'
author: 'Brad Carter'
date: '5 January 2021'
---

I recently read [this great blog post by Jeff Magnusson](https://multithreaded.stitchfix.com/blog/2016/03/16/engineers-shouldnt-write-etl/) entitled Engineers Shouldn’t Write ETL. It does a great job of explaining a lot of my frustrations with my current work. In this post, I want to add some of my own thoughts to the discussion about the Thinker/Doer anti-pattern.

#### What is Thinker/Doer?

Thinker/Doer is a naturally occurring organizational anti-pattern that frequently crops up in business intelligence and data science organizations.

Most instances of the Thinker/Doer pattern start out similarly enough. A group of business users need to make a business decision and they want to do it in a data-driven way. However, the analysis that they need to perform has outgrown what they can do in Excel. At that point, some enterprising business user goes to the nearest C-level executive and says something along the lines of “This analysis is very important for X, Y, and Z reasons, but it’s too much effort for us and we’re also really busy doing all of these other important things too. Can we please hire a developer to write it for us?”

From that point forward, business users take on the role of Thinkers who generate ideas that need to be validated, while the newly acquired software engineers take on the role of the Doers who implement, test, and productionalize those ideas.

Thinker/Doer tends to look really good on paper. As a business manager, you’re freeing your analysts up to go think up more innovations that will make the business better, and you’re outsourcing all your code to a development team who apparently enjoys that kind of thing. Everybody is happier and the system is so much more efficient, right?

Well, no, not really. In practice, a collection of problems tends to crop up in Thinker/Doer systems over time and those problems usually prevent the system from bearing the fruits that were promised by the pattern in the first place. Let’s look at three of the big ones.

#### First, Doers tend to have above average turn over.

Take a moment to think about the most talented software developers that you know. One of the most common denominators that I have observed between the most skilled and innovative engineers that I’ve worked with has been a need to be challenged and engaged by their work. In short, the best developers need to work on challenging puzzles to be happy in their work.

Now take a moment to consider the ETL pipelines that constitute most of the work that Thinkers ask Doers to build for them. Would you consider it to be particularly challenging or interesting? I don’t. Jeff Magnusson doesn’t either. My favorite paragraph from _Engineers Shouldn't Write ETL_:

> In case you did not realize it, [n]obody enjoys writing and maintaining data pipelines or ETL. It’s the industry’s ultimate hot potato. … For the love of everything sacred and holy in the profession, this should not be a dedicated or specialized role. There is nothing more soul sucking than writing, maintaining, modifying, and supporting ETL to produce data that you yourself never get to use or consume.

Let’s consider one more characteristic of the most talented engineers and developers: they have other job opportunities. There are ten thousand other tech companies out there who will gladly snatch up the best developers at your company if they are given the chance. If your best developers (or any developers for that matter) are working exclusively on ETL pipelines, I don’t think that you have a right to be surprised when they leave your company for another that will give them interesting problems and fulfilling work to do.

#### Second, the cost to ramp-up a new Doer is huge.

When I started with my first team at Microsoft (an ETL engineering team composed of Doers, although I didn’t know what those words meant at the time), I was separately pulled aside by three senior team members and told that it was probably going to take 6 to 8 months to get to a point where I could begin to work on my own, and that I couldn’t let myself get discouraged between now and then. Since then, I’ve been transferred to two other ETL teams within my organization, and one of the most surprising lessons that I’ve learned is that that experience isn’t an outlier in ETL engineering circles. Additionally, while it can take many months to gain the basic understanding needed to work on ones own, it can take years to really understand an ETL system to the point where an engineer can make sweeping changes or to extend the system in a substantial way. To understand why this is the case, consider the following diagram:

![](https://i.imgur.com/C4OMMq5.jpg "Thinker/Doer Org Diagram")

In most business intelligence organizations, a single ETL engineering team will usually support at least several business groups that are trying to do analysis on different areas of the business. That engineering team will usually have a common ETL engineering platform consisting of tools like a Databricks Cluster, SQL Server instances, and a telemetry account among other tools. This cross-cutting platform supports the various ETL pipelines that are requested by the Thinkers in the business groups. In turn, those pipelines power visualization tools like Tableau and PowerBI dashboards that business leaders use to make decisions.

There are two reasons why the ramp up time is so high for Doers:

-	First, maintaining and extending the core platform is actually a pretty small fraction of ETL engineering work. Most Doer time is actually spent maintaining and extending each of the ETL pipelines that are built on top of the platform. To care for those pipelines, Doers have to become intimately familiar with the business context surrounding each pipeline. While this arrangement could be workable if the Doers were limited to half dozen or so ETL pipelines, it is important to note that the above diagram is not drawn to scale. It’s not uncommon for large business intelligence organizations to have a dozen different business groups, nor is it uncommon for each of those business groups to accumulate many dozens to hundreds of ETL pipelines over the space of a few years. The reason that new engineers need so much time to ramp up is that they must become familiar with the business context surrounding each of those many hundreds of ETL pipelines.

-	Second, between the requests for new pipelines and modifications to existing pipelines, development teams rarely have sufficient time to properly maintain the base platform. The resulting cruft and technical debt also tend to increase the ramp-up time for new team members.

This ramp-up time can cause significant delays for the business. Let’s consider some scenarios where we would need to suddenly add new developers to an existing team. Maybe the team was recently assigned some new high priority responsibilities, or maybe several developers realized that they were tired of working on ETL and went to work for different companies around the same time. In either case, we now need to fill the holes in our development budget. We can do this by either reassigning engineers from other teams or we can acquire new engineers from outside the company. In either case, the new engineers won’t be terribly productive because most of their time will be spent just trying to gain context on the business needs surrounding various ETL pipelines. To make matters worse, the productivity of the wider team will probably also take a hit since they will be spending a significant amount of time helping their new colleagues as they ramp up.

Eventually, the team’s productivity will recover. Hopefully, your customers will stay with you in the 6 or more months between now and that point though.

#### Third, Thinker/Doer doesn’t scale.

As your business grows (or more specifically, as your business intelligence needs grow), Thinkers and their ideas tend to multiply like rabbits. Existing business groups tend to grow. Enterprising Thinkers will go off and start new business groups which are then staffed with new Thinkers. On top of that, your existing Thinkers are still constantly spinning off new ideas. (That is their job description after all).

All of this would be ok if we could recruit new Doers at the same pace that we recruit new Thinkers. Sadly though, that’s not the case. It’s difficult to find skilled developers on a good day, and ETL teams are never blessed with the best of circumstances. When job candidates discover that your “Software Engineering” job posting is really an ETL Engineering job posting in disguise, growing Doer teams goes from being merely difficult to nearly impossible.

While Doer teams will still occasionally be able to acquire new developers, the long acquisition process combined with developers frequently leaving to go work for other companies results in a growth rate that ranges from glacial to non-existent. The result is a more-or-less fixed sized Doer team supporting an ever-growing list of new features from an ever-growing Thinker team, as well as maintaining an ever-growing body of existing ETL pipelines.

With Thinker/Doer organizations, the question is never “Will the Doer’s be able to keep up with the demands of the Thinkers?” Rather, the question is always, “When are the Doer’s going to get buried by the work queue?”

Ultimately, the imbalance between the rate at which Thinkers can generate ideas and the rate at which Doers can implement them can have a significant impact on the culture of your business and especially on the morale of your Doers. Let me illustrate this with a personal example.

In much of Microsoft (my current employer, if that isn’t clear from context), long term work planning is done in terms of six-month semesters that go from January to June and July to December. Before each semester, teams put out calls for major feature requests so that estimates can be made and work can be prioritized. When a business user submits a new feature requests, he or she also attaches a priority ranging from 0 to 2. Priority 0 requests are business critical features that are needed to maintain or avoid losing existing value, priority 1 requests are new features that promise to add significant amounts of new value, and priority 2 requests are everything else.

Before the January 2021 semester started, my boss took most of November to estimate and prioritize our work requests. When she got back, she informed us that, by her estimates, our team would need four times as many engineers as we currently have just to address just the priority 0 requests. Understandably, my teammates and I all became somewhat nervous, and to my boss’s great credit, she immediately told us that she had already sent out notes explaining that we were severely over capacity and would not be able to work on most of the requests we had received. (If my boss is currently reading this, thank you :).)

While this thankfully isn’t the case in my workplace, it’s not hard to imagine other workplaces where the misaligned schedules and dropped feature requests could generate a lot of friction and a generally adversarial relationship between the Thinker and Doer groups. In my mind, it isn’t particularly hard either to imagine such a hostile workplace driving out Doers at an even faster rate.

#### So what’s the alternative?

In Jeff Magnussons words, the solution is to give your Business Users full ownership over (and thus responsibility for) their data, including the ETL pipelines that produce it. There are no more Thinkers. Rather, there are Data Engineers who own and maintain a core ETL platform and Business Users who leverage that platform to collect, process, and aggregate the data that they need to make their decisions.

I think that this arrangement addresses each of the above-mentioned problems directly and succinctly. First, it’s substantially easier to recruit new talent when you can say “**DOES NOT WRITE ETL**” in big, bold letters at the top of your data engineer job listings, and it’s also much easier retain the talent that you recruit when those engineers are able to work on broadly applicable problems and cross-cutting concerns instead of data pipelines that they don’t personally use or understand that well.

Second, data engineers will be substantially more productive (and happier) when they can get to work immediately without having to understand the business context surrounding each of the hundreds of ETL pipelines that exist in the company. Additionally, the data engineers can now focus on refining the platform and thereby delivering benefits to all users of the platform instead of just taking care of the needs of any one business group.

Finally, the business intelligence team is no longer being bottle necked by a single, understaffed development team, meaning that work can happen more quickly, and in accordance with the needs and priorities of the business teams instead of those of the development team. Additionally, by spreading the understanding of your ETL pipelines out among your broader business intelligence team, you eliminate a dangerous single point of failure that could cripple the organization if too many developers leave at the same time.

#### One last note.

This proposal will probably not be popular with your Thinkers, or at least not initially. After all, who would want to change a status quo where their job is to think up cool ideas and then watch as an army of developers takes care of the implementation details for them?

If you’re trying to drive this change in your team or company though, it’s important to stress that this that idealized Thinker/Doer model was never going to happen anyway. Instead, you need to stress that doing away with Thinker/Doer is the only sustainable way of preventing your development team coming to you and saying that they are 400% over capacity and won’t be able to accept new work requests for the next 6 months while they get the work queue back under control.
