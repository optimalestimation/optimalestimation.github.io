---
layout: post
title: The Three C's of Caches
categories: computer-architecture, power
---

Compulsory miss, Capacity miss, and Conflict miss for a Cache are already well documented in the literature. 

The main question is how do we measure what is causing the cache misses in our system? Can we do something about it? Do we need to increase the cache size? Or change the cache eviction policy? 

If it is a compulsory miss, there is nothing we can do. We can measure such misses by simulating a case with an infinite cache. 

Next, we can determine if our cache size is sufficient using a fully set-associate Cache. Here, we replace the least recently used Cache block. Any additional misses over the compulsory misses are due to the cache size. We can optimize for these misses by increasing Cache size. 

Finally, the remaining misses in the system would happen due to other assumptions on the Cache architecture, such as n-set-associativity and Cache eviction policies. We can change these to optimize for a given set of workloads. 