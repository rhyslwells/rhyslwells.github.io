---
classes: 
    - wide
    - dark-theme
title: "A Caution for the Over Reliable"
date: 2025-05-21
categories :
    - blog
tags: [data]
# toc: true
# toc_label: "Table of Contents"
excerpt: "A caution for those who quietly hold systems together."
header:
  overlay_image: 
  overlay_filter: 0.5 # same as adding an opacity of 0.5 to a black background
#   caption: "Random picture"
---

In many organisations, especially in operational or analytics-heavy environments, there’s a silent pattern that emerges: someone becomes the glue. They’re not formally promoted, not officially titled, but they **end up holding systems, processes, and people together**. This post outlines how that can happen, why it’s dangerous, and how easily it goes unnoticed-especially when you're effective at it.

### You Become the Glue

You don’t plan to be the glue. It happens gradually-through context, reliability, and necessity. A system lacks documentation, so you map it out to keep things working. A reporting pipeline is fragile, so you rewrite the formulas. An upstream change breaks a report, and you're the only one who knows how to fix it-not because it’s your job, but because you were the last one who figured it out.

The work is cumulative, and often invisible. Someone says, “This thing is broken,” and you patch it. Then next time it’s, “Why is it broken again?” and the patch needs context. The context lives in your head. You’re not just fixing tools-you’re **maintaining memory**.

### The Nature of Glue Work

What starts as a one-time assist becomes a permanent responsibility. You’ve written that Excel macro for monthly reporting. It works, but it’s built on specific quirks of your team’s file versions. You where only given a short period of time to build it and test it - therefore there is massive amounts of **technical debt**. Then a couple months later, someone pings you: “The numbers don’t match this time.” And you’re back in a file you haven’t opened in months, reinterpreting old logic with current expectations.

You built that process **once**-cleaning, aggregating, transforming the raw data into something presentable-but now you're expected to own it, indefinitely. The assumption is that if you touched it once, you must still remember it.

Documentation doesn’t scale linearly with work. When something feels like a one-off, you don’t invest in pristine documentation. But many one-offs eventually converge into critical infrastructure.

### When Maintenance Becomes Ownership

Over time, the work expands: a tracker here, a preprocessing script there, maybe a Word template that pulls from a very specific folder on the server. You're the only one who knows that folder exists, and the only one who can explain why the numbers look the way they do.

This hidden ownership turns reactive. You’ve gone from building things to spending your days reviving and interpreting them. You might manage dozens of mini-systems across Excel, Python, Google Sheets, or internal tools. None of them are documented to survive without you, and no one really knows what they rely on-until they break.

This is the trap. You weren’t assigned these systems. You became responsible for them because you were effective at solving the problems when they first appeared. But the cost compounds.

### Fragility in the System

Glue work can feel rewarding, until you realize how brittle the systems are around you. A dashboard fails not because of bad data but because someone renamed a file. A downstream dependency breaks when a formula is changed three layers up. AppSheets integrations crash when columns shift out of order, and you're the only one who remembers the correct structure-because the app doesn’t explain why it’s broken. You just know.

Stakeholders get what they need, eventually. But it's at the cost of your time, your memory, your energy (I hate to say it but your ... bandwidth). And in the absence of visibility, it doesn’t show up on any performance metric.

### Why It’s a Warning

This post is a caution. If you’re reading this and recognising these patterns in your own work, it might be time to step back. Document. Delegate. Or at least, surface the cost of your time. Because what you're doing is not just patching bugs or answering questions-you're providing **institutional memory**. That’s valuable, but it’s also risky.

Being the glue can feel like being useful. But glue hardens. And when you’re holding too much together, you become the **single point of failure** in systems no one else understands.

### Takeaway

**DataOps is the glue that holds operational infrastructure together.** But glue work is only sustainable when it's recognised, supported, and distributed. If you're the one holding it all together-step back, take stock, and make sure you're not holding it alone.

