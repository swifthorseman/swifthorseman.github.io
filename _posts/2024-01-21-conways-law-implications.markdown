---
layout: post
title: "Implications of Conway's Law"
date:   2024-01-21 10:00:00 +0000
categories: blog
---

> … organizations which design systems (in the broad sense used here) are constrained to produce designs which are copies of the communication structures of these organizations.
> &mdash;Melvin E. Conway [^1]

The above excerpt&mdash;what is now known as Conway's Law&mdash;has been cited more frequently in the past decade with the adoption of cross-functional teams in modern software engineering organisations. The usual explanation goes something like this: instead of having separate development, testing and product teams, it is both efficient and effective to form product-centric small teams consisting of developers, a QA engineer and a product owner. This eliminates bottlenecks and reduces cross-team chatter.

That framing is useful but narrow. Conway's Law has implications well beyond team composition. Hard boundaries between groups show up in the system, and so does how an organisation distributes authority, access and decision-making:

1. If there are separate testing and development teams, developers will throw deliverables over the fence and care less about quality because testing is the responsibility of another team.
1. If there is a divide between developers and operations, the former will tend to care about writing code and not about how the system behaves in production.
1. If the system is designed by a software architect in a silo, the system will likely lack testability and will miss logistical details.
1. If the team is not given autonomy to make engineering decisions, they end up doing just what they are told by the architect or the product team. They will not be able to take ownership when issues arise, nor will they grasp the bigger picture of what they are building.
1. If the team needs permission or budget approval to make the system robust, the system will be prone to outages in production and will create a bad user experience.

Simply putting people of different skill sets into a team is not sufficient to create a high-performing team. The team also needs the autonomy to make engineering decisions so that they can have accountability and ownership. And the wider organisation needs to respect those boundaries&mdash;resisting the urge to override technical decisions from above or gate them behind slow approval processes. Conway's Law tells us that if the communication structure is right, the system design will follow. The inverse is equally true.

---

[^1]: [How Do Committees Invent?](https://www.melconway.com/Home/pdf/committees.pdf)
