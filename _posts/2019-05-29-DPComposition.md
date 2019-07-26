---
title:  "Differential Privacy Part-III: Composition"
layout: posts
---

Composition is one of the major features of DP. This allows us to not only quantify how privacy is guaranteed for a single query or mechanism but a series of of them

Basic Composition
Simplest rule of them is basic composition , which states that if k DP algorithms are run the privacy is now

DP(k,k)

Composition takes into account two possible ways privacy could be degraded:

When the multiple queries are ran on the same database multiple times
Queries are run on seperate databases containing information on same individuals. It is also possible for adversery to influence creation of databases to learn about given target.
Advanced Composition
The basic composition could handle only linear possible degradation in privacy which may not be the case in practice. Introducing Advanced composition which could handle more advanced forms of privacy degradation. When an adversery ideally plans to learn about the database they don't typically do it linearly , they do in a fashion where they adapt better with increased number of queries. The adversery uses information from previous mechanisms and use information of current mechanism to learn in future mechanisms. Advanced composition given by


It is usually a pessimistic bound for understanding privacy degradation
