---
title: Cloud Fundamentals
date: 2023-09-22 22:00:00 -0300
categories: [Fundamentals, Cloud]
tags: [cloud]
mermaid: true
---

There's been a lot of talk about cloud computing lately, but what is cloud computing?

Cloud computing is the *on-demand delivery* of compute power, database, storage, applications, and other IT resources through a cloud services platform via the Internet with *pay-as-you-go pricing*. With cloud computing, you don’t need to make significant upfront *investments in hardware* and spend a lot of time on the heavy lifting of *managing that hardware*. Instead, you can provision exactly the *right type and size* of computing resources you need to power your newest idea or operate your IT department. You can access as many resources as you need almost *instantly*, and only *pay for what you use*. The cloud services platform provides *rapid access to flexible and low-cost* IT resources.

When we talk about cloud computing, we must master some terms that will help us better understand this matter.

- **High availability:** is a quality of cloud computing that allows us to keep our services available most of the time. In this way, the systems are designed to operate continuously without failures for a long time, which avoids the loss of these services by reducing or managing failures.

- **Elasticity:** is another quality of cloud computing with which it is not necessary to plan how much capacity we need. We can provision only what you need and then grow and shrink based on demand.

- **Agility:** It is defined as the ability to quickly build, test, and deploy applications and software in the cloud as you need it, often in response to market changes.

- **Durability:** is all about long-term data protection. This means your data will remain intact without corruption for a long time.

All these concepts are interrelated. For example, the ability to scale resources up and down quickly (**Elasticity**) is what allows us to keep our services available during periods of high demand (**High Availability**). All this with the possibility of launching new functionalities and new services very quickly (**Agility**).

There are other concepts related to the expenses incurred in cloud computing, which are also important to know,

- **CapEx:** Refers to the costs the organization must incur to purchase fixed assets that will offer ongoing, long-term benefits well past the current tax year.

- **OpEx:** Instead of revolving around one big bill up front, *OpEx* purchases are typically pay-per-use or subscription-based. That means *OpEx* assets are not the exclusive property of the organization that uses them but of the service provider.

---

The use of cloud computing allows us to bring many advantages; not only does it allow us to place our applications or services in various regions of the world (**Go global in minutes**), thus offering lower latency and a better experience to our customers at a minimum cost, but it also allows us to do all this at a lower cost (**Benefit from massive economies of scale**).

Additionally, it saves us from spending money on managing and maintaining data centers, allowing us to focus on our customers rather than having to lift, stack, and power servers (**Stop spending money running and maintaining data centers**). Let's focus on our business, not on the infrastructure.

On the other hand, it allows us (**Trade fixed expense for variable expense**), instead of investing heavily in data centers and servers, to be able to pay only when we consume computing resources and pay only for how much we consume.

Let's take the guesswork out of our infrastructure capacity needs (**Stop guessing capacity**). With cloud computing, these problems disappear. We can access as much or as little capacity as we need and scale it up or down as needed in just a few minutes. New IT resources are just a click away (**Increase speed and agility**), meaning you reduce the time to make those resources available to your developers from weeks to just minutes.

## Cloud Computing Models

- **IaaS:** Contains the building blocks for cloud IT, typically providing access to **network** functions, **computers** (virtual or bare metal), and data **storage** space. OS, configurations, and maintenance are the responsibility of the user.
- **PaaS:** Removes the need for the user to manage the underlying infrastructure (hardware & OS) and allows you to focus on deploying and managing your **applications** (**Data** and **Access**).
- **SaaS:** Gives you a complete solution managed and executed by the service provider, where you don't have to think about how the service is maintained or the underlying infrastructure is managed. Just provide the **data** to the application.

## Cloud Deployment Models

- **Private:** Services and computing resources used exclusively by users from one business or organization. It can be located in the organization (on-premises) or, it can be hosted in the cloud (dedicated cloud offered by cloud providers).
- **Public:** Services offered over the public Internet to individuals and organizations who wish to purchase. Cloud resources (computer, storage, network, and others) are operated by external providers (the owners) and delivered on demand.
- **Hybrid:** Is a combination of **public** and **private** clouds. The most common method of hybrid deployment is between the cloud and existing on-premises infrastructure to extend, and grow, an organization's infrastructure into the cloud while connecting cloud resources to the internal system.

## Regions

A **Region** is a physical location in the world that contains 2 or more Availability Zones. Each region is isolated and fully independent, so if one of them is affected, the others are not. Regions are grouped in geographically isolated locations around the globe, called **Geographical Locations**, On the other hand, most of the resources are tied to a specific Region, and you should set up resources in Regions closest to your users.

## Availability Zones(AZs)

They are a collection of **one** or **more** physically separate **data centers**, each with redundant power, networking, and connectivity housed in different facilities. AZs are connected through **low latency** links, are **fault-tolerant**, and allow *high availability*. An AZ is associated with a single Region.
