---
layout: post
title: "100% Unit Test Coverage versus Test-Driven Development"
date:   2024-01-01 22:00:00 +0000
categories: blog
---

Every once in a while, I come across developers who take pride in having 100% unit test coverage in their code base.  When such developers were asked whether they practise Test-Driven Development (TDD), their response would be ‘No,’ and that the unit tests were added after the code was written.

Writing unit tests after the code is written and chasing 100% coverage lead to meaningless tests.  To quote Dave Farley, “[you tend to only test that the code that you wrote is the code that you wrote.](https://youtu.be/ln4WnxX-wrw?list=PLwLLcwQlnXByqD3a13UPeT4SMhc3rdZ8q&t=385)”

Some organisations are obsessed with 100% test coverage and use this metric as an indicator of a healthy code base.  It will not be long before the metric is gamed by development teams.  With unit test generators, it is only too easy.  

Practising TDD means your code is driven from the specifications that you stated in the form of unit tests.  The tests will fail at first (since you have not written any code), so you write code to fix those failing tests.  As a by-product of TDD, you get 100% coverage.  The code written out of TDD is more testable and is easy to refactor, hence it is easier to maintain and extend.

Instead of chasing only 100% test coverage, if the efforts are placed more on ensuring engineers receive training to practise TDD, it will result in a healthier code base and an increased developer productivity, which will lead to adopting Continuous Delivery. [^1]

---

Thanks to Krishna Sowjanya Chandrappagari for reading drafts of this.


 [^1]: Continuous Delivery: "Working in small steps so our software is ALWAYS in a releasable state"&mdash;Dave Farley in [Continuous Delivery Pipelines: How to Build Better Software Faster at GOTO 2021](https://youtu.be/eoaDr5PpT2c?t=502)

