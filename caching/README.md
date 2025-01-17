### Cashing
Caching is a technique used to store and reuse the results of expensive or frequently accessed operations to improve performance. Instead of recalculating or fetching data repeatedly, caching stores the data in a temporary storage area (cache) and retrieves it when needed. Python provides built-in support for caching through modules like functools.lru_cache and libraries like cachetools. These tools help manage cache efficiently by limiting its size and removing old or less frequently used entries based on predefined strategies.

A cache works by associating keys with values. When a program requests a value, it checks the cache first. If the value is found (a "cache hit"), it is returned immediately. If not (a "cache miss"), the program computes or fetches the value and stores it in the cache for future use. Effective caching strategies ensure the cache remains performant by balancing storage size and the likelihood of cache hits.

## FIFO (First-In-First-Out)
The FIFO caching strategy removes the oldest entry from the cache when it reaches its capacity. This approach is straightforward, assuming that the first item added is the least likely to be used again. However, FIFO does not consider how often or recently an item is accessed, which can lead to suboptimal performance if older entries are still relevant.

Example: If a cache has a size limit of 3 and stores [A, B, C] in order, adding a new item D will remove A, resulting in [B, C, D].

## LIFO (Last-In-First-Out)
LIFO removes the most recently added item from the cache when it becomes full. This strategy assumes that newer items are less likely to be reused than older ones. While less common in practice, LIFO can be useful in specific scenarios where recently added items are truly disposable.

Example: If the cache holds [A, B, C] and item D is added, C (the last item added) will be removed, leaving [A, B, D].

## LRU (Least Recently Used)
The LRU strategy evicts the least recently accessed item when the cache is full. This approach assumes that recently used items are more likely to be accessed again. LRU is widely used because it balances simplicity and performance, especially for applications with predictable access patterns.

Example: If the cache contains [A, B, C] and B is accessed, the order becomes [A, C, B]. Adding D removes A, resulting in [C, B, D].

## MRU (Most Recently Used)
The MRU strategy removes the most recently accessed item when the cache is full. It assumes that the most recently used item is less likely to be needed again. This method is suitable for specific scenarios where older items are consistently reused, but it is less common than LRU.

Example: If the cache contains [A, B, C] and C is accessed, adding D will evict C, leaving [A, B, D].

## LFU (Least Frequently Used)
LFU evicts the least frequently accessed item when the cache is full. This strategy prioritizes items that are accessed more often, regardless of when they were last accessed. LFU works well in scenarios where some items are accessed repeatedly over a long period.

Example: If the cache holds [A, B, C] with access counts {A: 3, B: 1, C: 2}, adding D removes B, resulting in [A, C, D].

## In Summary
Caching strategies like FIFO, LIFO, LRU, MRU, and LFU are essential for managing limited cache space efficiently. Each strategy suits different access patterns and workload characteristics, and the choice of strategy can significantly impact application performance. Python's functools.lru_cache and libraries like cachetools allow developers to implement these strategies with minimal effort.