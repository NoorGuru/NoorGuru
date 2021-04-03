---
title: "Scalability 03 | Scale Vertically (Vertical Scaling)"
date: 2021-04-03T23:51:58+03:00
aliases: ["/sd/3", "/scalability/3"]
tags: [""]
categories: ["System Design"]
series: ["Scalability"]
hideSummary: false
summary: "Once your application (website) reaches the limits of your server, you should decide how to scale.
In this post, we will focus on Vertical Scaling only."
---

## Introduction

Once your application (website) reaches the limits of your server, you should decide how to scale.

> *You may find this useful:* [When (and Why) to Scale?](/posts/system-design/scalability-start-small-single-server-configuration/#when-and-why-to-scale)

There are two different types of Scaling:
1. Vertical Scaling
2. Horizontal Scaling

In this post, we will focus on ***Vertical Scaling*** only.

---

## What is Vertical Scaling?

You can scale your server vertically by upgrading the hardware and/or network throughput.
  
---


## Why to Scale Vertically?

- It's the *simplest* solution for *short term scalability*.
- It does not require architectural changes to your application (You don't have to rewrite all (or some parts) of your
  application). All you need to do is to replace a piece of hardware with a stronger or a faster one.


---

## How to Scale Vertically?

### 1. Add More I/O Capacity by Adding More Hard Drives in **RAID** (Redundant Array or Independent Disks) Arrays
- This is an important step as **the I/O throughput and disk saturation are the main bottlenecks in database servers**.
> *You may find this useful:* [What is RAID?](https://en.wikipedia.org/wiki/RAID)
- **RAID 10** is the most popular option is it gives both redundancy and increased throughput.


### 2. Use **SSD** (Solid-State Drives) to Improve I/O Access Times
- Random reads and writes are 10-100 times faster in SSD compared to normal Hard Disks (HDD).
- Sequential rear and writes are not much faster in SSD, and there will be no massive performance boosts in real world.
    - This is especially important when we know that most open-source databases are optimized to allow more sequential
disk operations (reads and writes) than random ones. Some databases use only sequential operations!
    - This makes upgrading from **HDD** to **SSD** a harder option to recommend. 


### 3. Increase **RAM** to Reduce I/O Operations

- Memory size is super important for efficiency of database servers.
- More memory means more space for the file system **cache** and more working memory for the application.


### 4. Upgrade Network Interfaces or Install New Ones to Improve Network Throughput

- This is especially important if your application is streaming a lot of video or media content.
- You could upgrade your network provider connection or upgrade your network adapters.

### 5. Switch to More Capable Servers 

- This includes switching to servers with more processors or more (virtual) cores.
- The more CPUs and virtual cores, the more processes that can be executing at the same time (this will help in avoiding
  concurrency issues and limits).
- Your system will be faster since:
    - Fewer processes will have to share the same CPU or core.
    - Operating System will have to perform fewer context switches to execute multiple processes on the same core.

> *You may find this useful:* [Context Switch](https://en.wikipedia.org/wiki/Context_switch)


---


## Why NOT to Scale Vertically?

### 1. Cost

The main disadvantage of vertical scaling is that it becomes extremely expensive beyond a certain point. Thus, be careful
that we said *beyond a certain point** is in the start, it could be the most affordable scaling option to follow!

A simple example of that is upgrading your server's RAM, as it will start cheap when, for example, you upgrade from a 
4GB RAM (approximately $15) to 8GB RAM (approximately $40). But it may be not an easy decision to go from 128GB
(approximately $3000) to 256GB (approximately $18000) as it won't worth the upgrade!

### 2. Vertical Scaling has a Hard Limit

No matter how much money you may be willing to spend, it is not possible to continually add memory, CPUs, cores, and
hard disk drives. At a certain point you won't find a hardware available to support further growth.

### 3. OS or Application May Prevent You from Scaling Vertically

Some application designs may benefit nothing by adding more CPU or cores, especially the ones related to handle concurrent
behavior and threads. Thus, you may need to check the design of your application and any dependencies or other systems that
you are using before consider vertical scaling (this become more important as you reach more advanced stages of your growth).


---

## What are Other Available Options?

That's what we are discussing in this [Scalability Series](/series/scalability/). Stay tuned for more contents.

---

## Resources
- [Web Scalability for Startup Engineers (Book) 1st Edition. By Artur Ejsmont](https://www.amazon.com/Scalability-Startup-Engineers-Artur-Ejsmont/dp/0071843655).