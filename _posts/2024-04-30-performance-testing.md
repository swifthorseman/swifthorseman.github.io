---
layout: post
title: "Performance Testing: An Important Quality Stage Gate"
date:   2024-04-30 09:00:00 +0000
categories: blog
---

When running production systems, it is crucial to be aware of the capacity of the system, as well as its behaviour with respect to volume of traffic.  Sometimes, engineering teams tend to deprioritise implementing this important stage gate before going live, or not incorporate it in the deployment pipeline, reasoning that their system is not expecting a high volume of traffic, therefore there is little to be concerned about.  There are a few issues with this.

Firstly, when going into production, how will the system be provisioned?  How many pods is it going to be running on if it is going to be deployed on Kubernetes?  If deploying on EC2 in AWS, what is the instance type it is going to run on?  The instance type chosen on EC2 will affect the cost.  Is the system memory-bound or CPU-bound?  If we approach it from another angle, what is the budget allocated for running the system?  Can we run it within the allocated budget?

Secondly, how does the system behave?  The system in this context is a set of components required to provide functionality, which includes not only the application but also things like a log forwarder, a database, proxies and so on.  In JVM-based applications, how does the garbage collector behave?  Is the application releasing memory at the same rate as it is acquiring?  For the same volume of traffic, is the behaviour of the system consistent in terms of resource usage in a prolonged period?

Say one of the components of the system has a memory leak.  Such a resource leak would go undetected under normal traffic load until it breaches a threshold after a certain period.  For example, under normal traffic load, a memory leak would take one month until the memory runs out.  What performance tests provide is to speed up that discovery, effectively contracting time.

Thirdly, customers or the users of the system would also want to know the capacity constraints of the system.  Before signing a contract, the Service Level Agreements must be agreed upon.  Without understanding the behaviour of the system, it would be premature to agree on Service Level Agreements.

Performance testing is a very broad term.  There are various tests that fall under the term.  In _Continuous Delivery_[^1], Dave Farley and Jez Humble outlined four tests to measure capacity of a system as follows:

> * Scalability testing. How do the response time of an individual request and the number of possible simultaneous users change as we add more servers, services, or threads?
> * Longevity testing. This involves running the system for a long time to see if the performance changes over a protracted period of operation. This type of testing can catch memory leaks or stability problems.
> * Throughput testing. How many transactions, or messages, or page hits per second can the system handle?
> * Load testing. What happens to capacity when the load on the application increases to production-like proportions and beyond? This is perhaps the most common class of capacity testing.

These four tests are by no means all that there are, but they give us a good start.  Going with these, first and foremost, we need to be able to answer “How many transactions, or messages, or page hits per second can the system handle?”  The benefits of performing this test on a minimal set of components required to run the system without scaling out or up is that it gives us a benchmark, which will then be useful for performing scalability testing.  From that point on, we will be in a good position to continue with longevity testing and load testing.[^2]  In addition, it is also important to look at the metrics in production and fine tune the system and reiterate.

As the system goes through changes and evolves, its performance also changes: memory footprint, CPU utilisation and network usage may all change.  Even if there are no code changes, for every living system, we need to keep the dependencies up-to-date and patch the operating system on a regular basis.  More importantly, when security vulnerabilities are discovered, it is no longer an option to keep the system frozen.  Therefore, performance testing is a very important quality stage gate on the path to production.  As such, it should not be treated as a box-ticking exercise which one does once before going live, or as something that is done once in a while, but be implemented as a stage gate in the deployment pipeline.

---

Thanks to Stephen Day for reading drafts of this.


[^1]: Continuous Delivery: Reliable Software Releases through Build, Test, and Deployment Automation by Jez Humble and Dave Farley (Addison Wesley). Copyright 2011 Pearson Education, Inc., 9780321601919

[^2]: In most cases, reproducing the production traffic volume or replicating a production environment may not be practicable or cost-effective.  For example, reproducing a production-like traffic volume of Facebook or a production-like environment will be near impossible.  By testing on a system that is composed of a minimal set of components without scaling out or up, it is easier to understand its behaviour and extrapolate.  Although it will give some idea and confidence, large scale distributed systems like Facebook would perform canary testing at a regional level.
