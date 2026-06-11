# System Design Framework — what you need to know for the interview

## Why this matters
System design interviews test your ability to think through large-scale problems methodically. Without a structured approach, you will either freeze up or dive into implementation details that don't matter.

## The concept
The Hello Interview framework breaks every system design problem into five sequential steps: Requirements (what are we building?), Entities (what are the core data objects?), APIs (how do clients interact?), High-Level Design (what are the major components?), Deep Dives (pick 2-3 components to explore in detail). Each step builds on the previous one. You cannot skip steps without creating gaps in your reasoning.

## In the Hello Interview framework, this shows up at:
This IS the framework. Every other system design concept — load balancing, caching, database sharding — slots into one of these five steps. The framework gives you the scaffolding to organize technical decisions coherently.

## The decision you will need to make
When to spend time vs when to move forward. Each step has a natural stopping point where additional detail doesn't add value. Requirements should take 5-7 minutes. Entities should take 3-5 minutes. APIs should take 8-10 minutes. HLD should take 15-20 minutes. Deep dives fill the remaining time. Going too deep too early kills your ability to show breadth.

## A concrete example
"Design Twitter" breaks down as: Requirements (users post tweets, follow others, see timeline), Entities (User, Tweet, Follow relationship), APIs (POST /tweets, GET /timeline), HLD (web servers, tweet service, timeline service, databases), Deep Dives (timeline generation algorithm, tweet storage sharding). Each step answers different interviewer concerns — requirements show you understand scope, entities show data modeling, APIs show interface design, HLD shows architecture thinking, deep dives show technical depth.

## What a senior answer sounds like
"Before I start designing, let me clarify the requirements. Are we optimizing for read-heavy or write-heavy traffic? Should I assume this is a global system?" Then: "I'll work through this using a structured approach: requirements, core entities, APIs, high-level architecture, then deep dive into the most critical components."

## What to avoid
• Jumping straight into databases or architecture without establishing requirements
• Spending 20 minutes on requirements when the interesting technical problems are elsewhere

## Write it from memory
Close this tab. Open a blank document. Write out the five framework steps, their time allocations, and the exact interview language from this post — no notes.

In a real SD interview you will not have a reference. Practice retrieving this, not just reading it.