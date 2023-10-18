---
layout: post
title: Cache Memory Structure
categories: computer-architecture, power
---

The CPU core will generally send an instruction to load data from some main memory (RAM) address. How would this main memory address be modified for cache access? 

The memory address is divided into three parts - Set Index, Block Offset, and Tag. 

Consider a cache as a table storing data. A set is a row in a Cache memory table. The block or cache line size is generally 64 bytes. One set (row) of the Cache stores a cache line or a block. One column of the cache memory table stores 1 byte of data. This implies we have 64 columns. How do we know the number of sets?

The size of cache memory table = Number of sets $\times$ Block size

Assume a 64 KB Cache size. The number of sets (or rows in the table) for this Cache is 64KB/64B= 1024. 

Next, let us answer how many bits in our main memory address are used for our Cache with 1024 set of blocks size 64 bytes. Consider a main memory address of 32 bits. To identify a unique row in the table (set), we need 10 bits index, since the number of sets = 1024. Similarly, we need 8 bits offset to uniquely identify each of the 64 columns of a block. 

Out of the 32 bit, we only need the lower 10+8 = 18 bits to address the Cache. What about the rest of the 32-18 = 14 bits?

As you can notice, two unique 32-bit addresses with the same lower 18 bits can map to the same cache cell. This is expected because a cache size is a subset of the main memory size. We store the rest of the 14 bits as a tag. When we access one memory address, we reserve its full Block in the set and keep its tag in the tag directory (number of rows = number of sets). Next time, we will have a Cache hit when we access another memory address within the same Block. If we access a new memory address with the same set and block offset but a different tag, we call it a cache miss. Then, go to main memory, fetch that entire Block with new tag, and store it in the same set index. 
<!--
TODO: Add figure showing an address with three different fields. 
-->

So far, the type of Cache we looked at is called a direct mapped cache (a.k.a. 1-way set associative Cache). Notice the extra power we burn in storing the tags. 

# Set Associative Cache

We can store multiple tags in a single row of the cache table. A 2-way set associative cache would mean we store two tags and two blocks of Cache for each row in the table. In this case, the number of sets will drop to half for the same cache size. The address decoder logic will become more complicated, and we will store two times more tags. As a result, we will burn more power. 

However, this can increase performance (higher hit rate) because we do not have to evict the older Block with a different tag. In our temporal locality case, if we access that same Block sometime very soon, it is nice to have it stored in the Cache instead of evicting it for another Cache block.  

Similarly, a n-way set associative Cache can be built. Each set will have n-Cache blocks. The power consumed is way higher in this case, so performance gains might not be significant. 

In an extreme case, we can even construct a fully associative cache! Use a single set with all Cache blocks and directly compare tags to see which one needs access. The main memory address will not require a Set index field for this case. The number of Cache blocks will be determined by the Cache size. Correspondingly, we will choose the number of Block offset bits in the address. 

<!--
TODO: Add a figure showing different types of Cache structures
-->