---
title: Cloud Fundamentals
date: 2023-09-22 22:00:00 -0300
categories: [Fundamentals, Cloud]
tags: [cloud]
mermaid: true
---

There's been a lot of talk about cloud computing lately, but what is cloud computing?

Cloud computing is the *on-demand delivery* of compute power, database, storage, applications, and other IT resources through a cloud services platform via the Internet with *pay-as-you-go pricing*. With cloud computing, you don’t need to make significant upfront *investments in hardware* and spend a lot of time on the heavy lifting of *managing that hardware*. Instead, you can provision exactly the *right type and size* of computing resources you need to power your newest idea or operate your IT department. You can access as many resources as you need almost *instantly*, and only *pay for what you use*. The cloud services platform provides *rapid access to flexible and low-cost* IT resources.

***When we talk about cloud computing, we must master some terms that will help us better understand this matter.

- **High availability:** is a quality of cloud computing that allows us to keep our services available most of the time. In this way, the systems are designed to operate continuously without failures for a long time, which avoids the loss of these services by reducing or managing failures.

- **Elasticity:** is another quality of cloud computing with which it is not necessary to plan how much capacity we need. We can provision only what you need and then grow and shrink based on demand.

- **Agility:** It is defined as the ability to quickly build, test, and deploy applications and software in the cloud as you need it, often in response to market changes.

- **Durability:** is all about long-term data protection. This means your data will remain intact without corruption for a long time.

All these terms are interrelated. For example, the ability to scale resources up and down the capacity (**Elasticity**) is what allows us to keep our services available during periods of high demand (**High Availability**). All this with the possibility of launching new functionalities and new services very quickly (**Agility**).

There are other concepts related to the expenses incurred in cloud computing, which are also important to know,

- **CapEx:** Refers to the costs the organization must incur to purchase fixed assets that will offer ongoing, long-term benefits well past the current tax year.

- **OpEx:** Instead of revolving around one big bill up front, *OpEx* purchases are typically pay-per-use or subscription-based. That means *OpEx* assets are not the exclusive property of the organization that uses them but of the service provider.

The use of cloud computing allows us to bring many advantages; not only does it allow us to place our applications or services in various regions of the world (**Go global in minutes**), thus offering lower latency and a better experience to our customers at a minimum cost, but it also allows us to do all this at a lower cost (**Benefit from massive economies of scale**). Additionally, it saves us from spending money on managing and maintaining data centers, allowing us to focus on our customers rather than having to lift, stack, and power servers (**Stop spending money running and maintaining data centers**). Let's focus on our business, not on the infrastructure.

On the other hand, it allows us (**Trade fixed expense for variable expense**), instead of investing heavily in data centers and servers, to be able to pay only when we consume computing resources and pay only for how much we consume.

Let's take the guesswork out of our infrastructure capacity needs (**Stop guessing capacity**). With cloud computing, these problems disappear. We can access as much or as little capacity as we need and scale it up or down as needed in just a few minutes. New IT resources are just a click away (**Increase speed and agility**), meaning you reduce the time to make those resources available to your developers from weeks to just minutes.

## Cloud Computing Models

Going a little deeper, in Cloud Computing, there are three models that define the deployment type of resources within cloud computing. These are *Private*, *Public*, and *Hybrid*.

A **Private Cloud** is when the infrastructure resources are offered over the Internet and are used by users of a single company or organization. This model can refer to local data centers (on-premises) or hosted in the cloud (dedicated cloud offered by cloud providers).

A **Public Cloud** is built, controlled, and maintained by a third-party provider and is offered over the public Internet to individuals and organizations who wish to purchase it. In this cloud model, resources (computer, storage, network, and others) are operated by third-party providers (owners) and delivered on demand, unlike an on-premise data center, where the company/organization is responsible for maintaining and replacing resources (computer, storage, network, and others) when necessary.

A **Hybrid Cloud** is a combination of both *Public* and *Private* clouds inter-connected. The most common method of hybrid deployment is when using the cloud and existing on-premises infrastructure, where users can flexibly choose which services to keep in the *Public* cloud and which to deploy to their *Private* cloud infrastructure, thus providing an additional layer of security.

## Cloud Computing Services Types

Regardless of the cloud model we use, there are three main types of services offered within cloud computing. These types of services help us understand the flexibility we have to manage and configure resources in the cloud.

**Infrastructure as a Service (IaaS)** is the most flexible type of cloud service, as it provides us with the maximum amount of control for our cloud resources. In this type of service, the Cloud Provider is responsible for maintaining the hardware, network connectivity (to the Internet), and physical security. We are responsible for everything else: operating system installation, configuration, and maintenance; *network configuration; database and storage configuration; and so on. With IaaS, we are essentially renting the hardware in the cloud, but what we do with that hardware is up to us.

**Platform as a Service (PaaS)** is a middle ground between *Infrastructure as a Service* and *Software as a Service*. When we use PaaS services, the cloud provider maintains the physical infrastructure, physical security, and Internet connection. It is also responsible for the operating systems, middleware, and development tools that are part of the cloud solution. In PaaS services, we do not have to worry about licenses or patches for operating systems and databases, and they are ideal for providing a complete development environment because they allow us to focus on deploying and managing our applications.

If we look at these service models as a pyramid, **Software as a Service (SaaS)** is at the top of the pyramid. SaaS services provide a solution fully managed and run by the cloud provider, where we don't have to think about how the service or underlying infrastructure is maintained. While the SaaS model may be the least flexible, it is also the easiest to get up since it does not require extensive technical knowledge or experience to use it.

## Availability Zones

Cloud providers are increasingly present in all parts of the world, and, to this end, they have various data centers spread around the world. These data centers are located in the same geographic space called **Availability Zones (AZ)**. AZ is nothing more than a collection of one or more physically separate data centers, each with redundant power, networking, and connectivity housed in different facilities. AZs that are located in the same *Region* are connected via low latency links, are fault-tolerant, and enable high availability.

## Regions

A **Region** is a physical location in the world that contains two or more AZs. Each Region is isolated and fully independent, so if one of them is affected, the others are not. Regions are grouped in geographically isolated locations around the world, called **Geographical Locations**. An important detail in cloud computing is that most resources are tied to a specific region, so a good practice is to configure resources in the Regions closest to the end users to whom the services will be provided are destined.
