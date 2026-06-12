# System Design Framework — structure for the interview

## Why this matters
System design interviews test your ability to architect large-scale systems under time pressure. Without a framework, you will ramble through requirements, miss critical components, or dive into implementation details too early.

## The concept
The Hello Interview framework breaks system design into five sequential steps: Requirements (functional and non-functional), Entities (data models), APIs (interface design), High-Level Design (architecture overview), and Deep Dives (scaling bottlenecks). Each step builds on the previous one. You move linearly through all five steps — no jumping around.

## In the Hello Interview framework, this shows up at:
This is the framework itself. Requirements clarify scope and scale. Entities define your data structure. APIs specify how components communicate. HLD maps the overall architecture. Deep Dives address specific scaling challenges the interviewer pushes on.

## The decision you will need to make
When to move from one step to the next versus when to stay and clarify. Move forward when you have enough detail to proceed — not when you have perfect detail. Stay when the interviewer signals confusion or when foundational assumptions are unclear.

## A concrete example
Design Twitter. Requirements: users post tweets, follow others, see a timeline. Scale: 100M users, 10M tweets/day. Entities: User, Tweet, Follow relationship. APIs: POST /tweets, GET /timeline/:userId. HLD: web servers, tweet service, timeline service, databases. Deep Dive: timeline generation — push vs pull model for follower feeds based on user follower count.

## What a senior answer sounds like
"Let me start with requirements to make sure we're aligned on scope. For functional requirements, I'm assuming users can post tweets and see a personalized timeline. For non-functional, I'm targeting 100 million users with 10 million tweets per day — does that scale sound right for this interview?"

## What to avoid
• Jumping to architecture before clarifying requirements — shows poor planning discipline
• Spending 20 minutes on data models — entities should take 3-5 minutes maximum

## Write it from memory
Close this tab. Open a blank document. Write out the key decision, the trade-off, and the exact interview language from this post — no notes.

In a real SD interview you will not have a reference. Practice retrieving this, not just reading it.