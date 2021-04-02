---
title: "Scalability 01 | What Is Scalability (in a Nutshell)?"
date: 2021-03-28T23:21:15+03:00
slug: "what-is-scalability"
aliases: ["/sd/1"]
tags: ["Scalability", "Concurrency", "Data", "Big Data", "Web Design", "Web"]
categories: ["System Design"]
series: ["Scalability"]
author: "Noor"
hideSummary: false
summary: "Scalability usually means the ability to handle more users, clients, data transactions, or requests without affecting the user experience."
---

## Introduction

> Things that can take an entire year in a corporate environment may need to happen in just a matter of weeks in a startup.

So that, you may need to *scale up* or *scale down* quickly, but what the scalability is even mean in a system design or
software engineering context?

---

## What is Scalability (in a Nutshell)?

**Scalability** usually means the ability to handle more users, clients, data transactions, or requests ***without affecting the user experience***.

What's described above is actually **scaling up**. Remember that you may need to scale down as well aiming to reduce unneeded expenses and efforts.

---

## How to Measure Scalability?
These measurements or data points could help us to measure the scalability of our systems:

### 1. Handling More (or Less) Data

In a website, for example, the ability to handle more user accounts, products, location data, and content efficiently
should measure the scalability of your website.

You should remember that we don't only to store these data, but to search, sort, process, and send it over the network.
All of this would contribute in the scalability of your website (system), especially in an era of BIG data.



### 2. Handling Higher (or Lower) Concurrency Levels

*How many users can use your application **at the same time** without affecting their user experience?*

You may need more resources (or better performance?) to handle more concurrent connections, active threads, messages
being processed at the same time, and more CPU context switches.

Limited resources (which will be almost always the case), makes this even harder!



### 3. Handling Higher (or Lower) Interaction Rates

*How often your clients exchange information with your servers?*

The importance of this should be higher in an online game that require multiple interactions per second, per user, than
in a website (like the one you are in right now) which may require a single interaction every ~30 seconds or even minutes.

In the online game example, we may need to work harder to achieve lower ***latency*** per request so that we can serve them
quicker, which indeed requires more ***concurrency***.


---
## Scalability VS Performance

These two concepts are obviously related, but we can differentiate between them as in the following:
- ***Performance*** measures how long it takes to process a request or to perform a certain task.
- ***Scalability*** measures how much we can grow (or shrink).

---
## Resources
- [Web Scalability for Startup Engineers (Book) 1st Edition. By Artur Ejsmont](https://www.amazon.com/Scalability-Startup-Engineers-Artur-Ejsmont/dp/0071843655).