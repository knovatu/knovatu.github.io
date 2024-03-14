---
title: Git Basic Commands
author: adejonghm
date: 2024-03-06 -0300
img_path: /assets/img/articles/git-basic-commands/
categories: [Git, Fundamentals, Basic-Commands]
tags: [git, fundamentals, devops]
mermaid: true
---

In my previous job, I had the opportunity to work with people of different profiles and, although I was within a consulting company, I could notice that many people did not know what Git is, what it is for, or how to use it. For this reason, I have decided to write about this topic, in an attempt to help those who still do not know what Git is and how to use it.

## What is Git?

A distributed Version Control System (SCM) is a tool that allows tracking of all changes in the source code and other files of a project regardless of its size and complexity, and it helps coordinate all work related to software development.

Git is a free and open-source SCM created in 2005 by Linus Torvalds as a solution to the challenges the Linux community faces in managing source code to develop the Linux kernel. Torvalds' idea was to build a distributed version control system that was robust, fast, and capable of handling large-scale projects with many contributors and development branches.

One of the nicest features of any distributed SCM, including Git, is its distributed nature. This means that each user working on a project has a complete copy of the repository, including the entire history of changes, on their local system, in contrast to Centralized SCMs, where a single central repository serves as a reference point for all users. These local copies of each user essentially act as a backup, which could be used to replace the version on the main server in case of failure or corruption.

Due to Git's distributed nature and branching system, it is possible to implement nearly infinite workflows with relative ease.

## Initial configurations

After learning a little about the history of Git, it's time to start understanding how it works. To do this, first of all, we must install Git on our operating system.

In this article, we do not cover installing Git. Therefore, we provide you with the official documentation to do so.

## Connection to remote repositories

## Basic Commands

## Terminology

- Branch:

- Commit: Um commit é uma operação no Git que registra uma alteração feita nos arquivos do projeto. Cada commit tem uma mensagem associada que descreve as alterações realizadas.

- Repositório: Um repositório Git é onde todo o histórico de um projeto é armazenado. Ele contém todas as versões dos arquivos, bem como as informações sobre quem fez as alterações e quando.
