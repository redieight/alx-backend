0x01. Caching
=
Cache replacement policies
=

This article is about general cache algorithms. For detailed algorithms specific to paging, see page replacement algorithm. For detailed algorithms specific to the cache between a CPU and RAM, see CPU cache.

cache algorithms (also frequently called cache replacement algorithms or cache replacement policies) are optimizing instructions, or algorithms, that a computer program or a hardware-maintained structure can utilize in order to manage a cache of information stored on the computer. Caching improves performance by keeping recent or often-used data items in memory locations that are faster or computationally cheaper to access than normal memory stores. When the cache is full, the algorithm must choose which items to discard to make room for the new ones.

The average memory reference time

 T = m x Tm + Th + E

 m = miss ratio = 1 - (hit ratio)

 Tm = time to make a main memory access when there is a miss (or, with multi-level cache, average memory reference time for the next-lower cache)

 Th= the latency: the time to reference the cache (should be the same for hits and misses)

 E = various secondary effects, such as queuing effects in multiprocessor systems

Simple queue-based policies
=

<h2>First in first out (FIFO)</h2>

Using this algorithm the cache behaves in the same way as a FIFO queue. The cache evicts the blocks in the order they were added, without any regard to how often or how many times they were accessed before.

<h2>Last in first out (LIFO)</h2>

Using this algorithm the cache behaves in the same way as a stack and opposite way as a FIFO queue. The cache evicts the block added most recently first without any regard to how often or how many times it was accessed before.

Simple recency-based policies
=

<h2>Least recently used (LRU)</h2>

Discards the least recently used items first. This algorithm requires keeping track of what was used when, which is expensive if one wants to make sure the algorithm always discards the least recently used item. General implementations of this technique require keeping "age bits" for cache-lines and track the "Least Recently Used" cache-line based on age-bits.

<h2>Most recently used (MRU)</h2>

MRU discards the most recently used items first. In findings presented at the 11th VLDB conference, Chou and DeWitt noted that "When a file is being repeatedly scanned in a [Looping Sequential] reference pattern, MRU is the best replacement algorithm."[8] Subsequently, other researchers presenting at the 22nd VLDB conference noted that for random access patterns and repeated scans over large datasets (sometimes known as cyclic access patterns) MRU cache algorithms have more hits than LRU due to their tendency to retain older data.