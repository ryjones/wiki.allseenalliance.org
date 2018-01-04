# Frequently Asked Questions

## Should all interfaces that get shipped in a product be reviewed by the IRB?

The IRB review process is required only for standardized interfaces. Any proprietary interfaces that go into a product are not required to go through an IRB review, but the IRB will gladly review (time permitting) any interfaces submitted at the request of a vendor. In any case, it is strongly encouraged that all interfaces follow the IRB guidelines regardless of whether they go through IRB review.

## I don't agree with the IRB's assessment of my interface definition. What happens now?

First of all, we're open for discussion. The Gerrit code review tool allows all interested parties to post comments on a submission, and it is trivial to reply to comments. If the IRB asks questions, or criticizes a design decision, do respond and defend your line of thinking. An open conversation will help us come to a consensus.

If you really can't see eye to eye with the IRB, the discussion can always be escalated to the Technical Steering Committee. Ultimately, the IRB's role is to advise the TSC on whether an interface is ready for standardization. If you don't agree with that advice, you are free to make your case directly to the TSC. No hard feelings.

## What happens when there is no progress in an IRB review?

We want to avoid that submissions get stuck in review indefinitely. Therefore, we have instituted the following policy:

*  The IRB will try to review any submission or update within 14 days.

*  If a submission or update is not reviewed within **30 days** it will be **automatically accepted**.

*  If a negative review (i.e. one that has at least one -1 vote from the IRB) does not see an update within **30 days** it will be **automatically abandoned**. *This does not preclude a later (updated) resubmission of the same interface.*

There is no overall time limit on the review process - as long as there is a constructive discussion on an interface, with frequent updates and reviews, the process can take as long as it has to. And remember, if it really isn't possible to come to a mutually agreeable resolution, there is always the option of escalating the matter to the TSC at large.

## The IRB often raises general system architecture issues during an interface review. I thought the IRB's mandate was limited to the review of interface definitions?

The overall system architecture of the AllSeen ecosystem is the responsibility of the Technical Steering Committee, not the IRB. However, due to the nature of its work, the IRB has a pretty good overview of the AllSeen system architecture, and that puts us in a prime position to spot conflicts and overlaps between different projects. Whenever the IRB spots such an issue, it will encourage the involved parties to work together on a common solution, and it will inform the TSC of any conflicts or issues it needs to weigh in on.

## The IRB complains about duplication of functionality. Why?

"Duplication of functionality" really means two things at different levels.

##### Within AllJoyn interfaces

It’s the IRB’s job to make sure that (in as much as this is possible, of course) there is precisely one standardized interface that offers a certain kind of information or functionality. It would be really bad if we’d let every project define its own interface for, say, temperature.

##### Across the Alliance as a whole

It is, in general, a sound engineering principle to make sure that responsibilities of individual components in a system are well-defined and that there is no overlap between those responsibilities. 

For example, the Core WG is working on Security 2.0 as a a framework-level approach to security. It would be bad if every individual project came up with its own approach to security that either completely ignores Security 2.0, or builds on it but in a totally different way than other projects build on it.

Analogously, if we have an Analytics project that is working on the standard way to approach analytics in the AllSeen ecosystem, it would be pretty bad to also have a standardized HomeController project that is defining a different way to approach analytics for Allseen in the smart home context. At the very least, there should be coordination and discussion between both projects.

## My project needs functionality that overlaps with functionality provided by another project, but that other project does not offer exactly what I need. What should I do?

From the IRB's point of view, we cannot let you define an interface that overlaps too much in functionality with what already exists in that other project. Here are some alternatives:

*  Contribute to the "competing" project! The Alliance is all about open source and collaboration, so this is really the obvious answer. Engage in a discussion with the other project, and figure out a way to combine your efforts on this front. Tell them which use cases aren't yet covered by their current road map, and offer to contribute an implementation. Of course, the realities of day-to-day project management dictate that there are deadlines to be made, and priorities to be set, but the sooner you start the conversation, the sooner your use cases will be covered in a release.

*  Define your overlapping interface, but don't submit for standardization. Every company is free to build whatever proprietary interfaces for its own use, and even to let others make use of these interfaces. Just don't use the ''org.alljoyn'' prefix for your interface names.

## My project will be defining a new interface that needs to be standardized.  When should I submit it for review?

As early as you possibly can.  AllJoyn interfaces greatly influence the architecture of the software that implements those interfaces.  If you wait until your project is nearly done, you may find yourself redesigning a lot of code that you have already written.

It is not important if you don't have all the details regarding the interface ironed out yet.  The IRB can assist you with that through our email list and gerrit reviews.
