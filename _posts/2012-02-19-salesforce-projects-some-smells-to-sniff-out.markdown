---
layout: post
title: "Salesforce projects - some smells to sniff out"
date: 2012-02-19 17:06
comments: true
categories: [salesforce.com, Force.com]
---

At [System Partners](http://www.systempartners.com) we've been doing Salesforce projects for quite some time. Some of us have been using it since 2002/3 I think. We've had the joy and pain of being involved with a lot of big and small projects.

Whenever a project requires something that is out of the ordinary we always shout out for an opinion in the team - this happens especially for non technical stuff. We stop tracks when someone says - hey I don't like the smell of this.

So what are some of those things we try to sniff out?

<!-- more -->

---

_This is an opinionated write up. I don't claim to be an expert. It may be totally incorrect from your point of view or I may have overlooked 10 other more important things. Please share your experience in the comments below._

---


## Initial phase

You spend time with the client to figure out what they want with the hope of providing an estimate of how long it will take and how much it will cost. After meeting the client and few requirements sessions you collate your notes and thoughts. 

Before delving into writing a statement of work (SOW) or detailed project plan you should be able to answer most if not all of these questions:

**1. In a sentence or two can you describe the aim of the project (not the system)?**

Try and focus on the underlying business problems and you need to clearly articulate them in plain english. Please don't use any 'cloud' derived words. A good example:

*The client wants to reduce the inventory in stock and use that inventory information to improve how they deal with their suppliers and customers.*

You want to achieve at least 2 out of the following 3 things - save money, make more money or put a smile on someone's face.

Based on the above example:

**Save money** - "reduce the inventory in stock"  
**Make money** - Not 100% clear. Perhaps we can assume that if customer dealings are improved they'll buy more next time or more often.  
**Make someone happy** - Again not 100% clear. Perhaps we can assume that if supplier dealings are improved then they'll be able to better manage their inventory.  

I've used a rather simple example. **Point being - the exercise of boiling it down to a few lines with the client's input is a very useful and hard thing to do**. This is especially useful in a large project where there is a seemingly endless list of things to achieve.

**2. What is the cost or impact of not doing the project?**

If the cost isn't high or well articulated then the client might not proceeed as quickly as you think they would/should. The client's enagagement is improved if they know full well the cost of inaction or delay.

**3. Who has ultimately commisisoned the project - cost or profit center?**

I find the cost center team a bit harder to negotiate with when it comes to keeping things simple. Perhaps they want to get the most out of their spend and want the investment to last for a while. This increases complexity impacting delivery. Profit center team typically want to see the project bear fruit quicker. This makes it a little easier to negotiate and simplify. 

Both camps have valid points of view. And before you get worked up I understand and appreciate that above is a gross generalization.

You need to make the client comfortable about iterating. A system never really stops from being improved.

**4. Of the impacted people, let's say end users, who has the most say?** 

Keeping the largest set of users happy is a good bet but also focus on the most powerful ones. You not only want the top sales person happy but also their personal assistant.

**5. What's the client's maturity in running projects?** 

Have you worked hard to deliver to a deadline only for the client to not be able to start the UAT for days or for the relevant stakeholders to be too busy to be actively involved?

The client's internal expertise in running Salesforce related projects matters. Do you need to educate the project manager to not bother testing saving of a record if there isn't any custom code tied to it? Salesforce have done that bit of testing for us.

Your main stakeholder's availability matters a lot. The project should benefit them directly.

There are obviously a ton of other questions to ask during this initial phase but above are few interesting ones to ask.


## Delivery phase

I think building systems with bit of pragmatism and little less code is always fruitful. **Salesforce's strength is ease of configuration to adapt to changing business needs and we should do everything to facilitate this.** For example, run a regular report to identify and clean up non-critical data rather than adding trigger based checks all over the place.

**1. If you migrate from an existing system to Salesforce then is data migration the last major activity?**

Imagine you just underwent training for the new Salesforce system in the full sandbox. Your login details have arrived in your inbox and you eagerly login to the new system. What do you think you'll do first? It's a good bet that you'll look for data that you had created previously. It's also a good bet that not finding that data would make you upset and not trust the system. This is no good and we want users to trust the system from the get go.

We found better results by bringing forward some activities typically carried out later in the project:

- Find the quickest path to get Salesforce up with all the data. Yes ALL the data.
- Figure out how to keep that data up to date with deltas of changed data or wipe and reload the data every so often.
- Get a pilot set of users to start using it.
- Progressively add business rules and chop and change things. Having business specific relevant data really helps in forming business rules. That trigger which fails during data migration will also fail much earlier on. Stakeholders are better able to say I really don't like where this field is placed or how this email template is setup.
- Create reports and dashboards.
- Tackle any integration work.
- Test. Seeing real data also allows users to better relate with what they are testing and they'll need less scripted instructions.

A lot of the above steps will be done in parallel but the focus is to bring the data migration step as far forward as possible.

**2. There's no data migration needed and majority of business problems are primarily solved with the use of Sales and/or Service cloud. Do you have more than 3 custom objects, triggers, Apex classes or Visualforce pages?**

Try to go live with none or minimal number of custom objects, Apex and Visualforce. Sounds like a silly arbitary rule. But it forces you to use the existing feature set. I have seen Opportunities being abandoned because Close Date always had to be there on the page layout. And then there is always an iteration after the pilot or go-live to add all the complex code you want.

**3. The project can't go live without full integration in place.**

Sometimes, but often it can. As long as you are not stopping the flow of revenue. If not creating an Opportunity with all the relevant data prevents an Order creation then yes integration is needed. But if it hampers marketing campaigns then maybe it can be added to the backlog with high priority.

**4. We're not sure what reports are needed but we know we can report on whatever we put into Salesforce.**

This is not a debate about Salesforce's reporting capability. It's more powerful than most people give credit for. The point is, let's say a field that the client expected to be in the report cannot be. As a quick win you perhaps recommend using Excel report. This becomes awkward if the client was told they don't need much of Excel anymore. So try and figure out the reports that are needed as soon as possible. It will also help to de-normalise early on.

**5. It's no point writing tests now because things are changing and the code is not settled.**

Even though test driven development is the way to go, sometimes things are indeed in a flux. At the very least try and maintain a good set of test data classes. So if you add a field ensure the test data has a valid value for that field. If the field type is changed ensure the test classes are updated too. Setting up test data IMHO is typically the hard part, writing assertions isn't.


## Rollout and post delivery phase

Depending on the size and scale of the project this phase could be quite chaotic and stressful. I get caught out off guard in this phase the most. Ever tried writing a rollback plan in case the weekend migration to the new Salesforce system doesn't go as planned? And then you actually have to action the rollback plan because there was an error in data extraction, which triggered a cascading set of errors. And no, aborting the rollout and turning the old system back on isn't always the best option. So here goes...

**1. The system will be maintained by the business and IT will not be involved.**

Sounds good but IT eventually will have to be involved. For example, upgrading to latest version of Microsoft Office might cause problem with document merge. Get them involved actively as soon as possible.

**2. We want our users trained quickly say in a 2 hour session?**

Possibly. But how about an overview and showing the users how to do 5 or 10 specific things in a one hour session. Record it and YouTube it so users can view it later. Let them use the system for a week and then have another session where you go through things in detail. I've been in long training sessions and after 90 mins I completely lose focus and end up on [Hacker News](http://news.ycombinator.org).

**3. Where are the release notes and user documentation?**

Remember the thing about Salesforce being easy to customize. A well written 100 page document will be out of date very quickly. How about adding lots of field help text and description instead. A good process diagram highlighting business rules is of great value.

**4. Our IT wants Salesforce to be managed like other software assets - we want everything to go via source control.**

This comes up surprisingly often with our clients. I have nothing against this except that Salesforce is unlike .Net/Java application. Not every setting is deployable via metadata API and that's OK. It increases the risk a little but there are effective ways to mitigate. [Sanpshot](http://appexchange.salesforce.com/listingDetail?listingId=a0N300000016YhyEAE) is worth considering. 

**5. I want PDF merging in batch mode or some other bit of functionality. Let's build it!**

Please head over to [AppExchange](http://appexchange.salesforce.com/home) first. If you don't find a solution, talk to partners who might be able to build an app and license it to you. The partner might get economies of scale and you don't have to maintain a product.

<br/>

---

_The overall aim is to deliver the project with minimum required deliverables and iterate. If you achieve the go live milestone with at least 15-20% of budgeted time to spare then you're doing great. It means you've delivered a cut down yet working solution. Improvements will be done based on a mix of actual user feedback, not assumptions, and existing backlog._

---

<br/>
I have left out a long list of things to look out for in every stage. Please share your experience in the comments below.
