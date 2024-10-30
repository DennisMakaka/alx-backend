# 0x01. Caching Project

### **Background Context**

This project covers different caching algorithms to implement and understand their benefits and trade-offs in various back-end contexts.

---

### **Resources**

- [FIFO Cache Replacement Policy](https://en.wikipedia.org/wiki/FIFO)
- [LIFO Cache Replacement Policy](https://en.wikipedia.org/wiki/LIFO)
- [LRU Cache Replacement Policy](https://en.wikipedia.org/wiki/LRU)
- [MRU Cache Replacement Policy](https://en.wikipedia.org/wiki/MRU)
- [LFU Cache Replacement Policy](https://en.wikipedia.org/wiki/LFU)

---

### **Learning Objectives**

By the end of this project, you should be able to:

1. Explain caching systems and their purpose.
2. Understand common caching algorithms:
   - FIFO (First In, First Out)
   - LIFO (Last In, First Out)
   - LRU (Least Recently Used)
   - MRU (Most Recently Used)
   - LFU (Least Frequently Used)
3. Recognize the limitations and potential of caching systems in terms of capacity and efficiency.

## Requirements
- **Python 3.x**
- The provided classes should inherit from the `BaseCaching` base class and adhere strictly to the required methods and cache management rules.
- Each class must handle over-capacity situations according to the specified caching strategy and print discarded keys when items are removed.

### Base Class: BaseCaching
`BaseCaching` is the foundational class, containing the shared data structure (`cache_data`) where items are stored. This class also specifies a maximum cache size, `MAX_ITEMS`, which is the limit at which the cache must discard items based on the active caching algorithm.

Each derived caching class inherits from `BaseCaching` and modifies the cache behavior by implementing different policies when items are added or retrieved.

## Tasks

### 0. Basic Cache
**Objective:** Implement a basic caching class, `BasicCache`, that inherits from `BaseCaching`. This class should store and retrieve items from the cache without any capacity restrictions.

**Method Requirements:**
- `put(key, item)`: Adds an item to the cache for a given key.
- `get(key)`: Retrieves an item by key from the cache.

### 1. FIFO Cache
**Objective:** Create a class `FIFOCache` that inherits from `BaseCaching` and follows the First In, First Out (FIFO) caching principle. When the cache reaches its capacity, the oldest item (the first added) should be discarded.

**Method Requirements:**
- `put(key, item)`: Adds an item to the cache, discarding the oldest entry when full.
- `get(key)`: Retrieves an item by key from the cache.

### 2. LIFO Cache
**Objective:** Implement `LIFOCache`, which inherits from `BaseCaching` and follows the Last In, First Out (LIFO) strategy. When the cache exceeds capacity, the most recently added item is removed.

**Method Requirements:**
- `put(key, item)`: Adds an item to the cache, discarding the most recent entry if full.
- `get(key)`: Retrieves an item by key from the cache.

### 3. LRU Cache
**Objective:** Design `LRUCache` class that inherits from `BaseCaching` and follows the Least Recently Used (LRU) policy. When the cache exceeds capacity, it should discard the item that was accessed least recently.

**Method Requirements:**
- `put(key, item)`: Adds an item to the cache, removing the least recently accessed item if full.
- `get(key)`: Retrieves an item and updates its access history.

### 4. MRU Cache
**Objective:** Develop `MRUCache`, inheriting from `BaseCaching`, to implement the Most Recently Used (MRU) caching strategy. When over capacity, the most recently accessed or added item is discarded.

**Method Requirements:**
- `put(key, item)`: Adds an item to the cache, discarding the most recently accessed item when full.
- `get(key)`: Retrieves an item and updates its access history.

### 5. LFU Cache
**Objective:** Implement an `LFUCache` class that uses the Least Frequently Used (LFU) caching algorithm. If the cache is full, discard the item with the fewest accesses. If there are multiple items with the same frequency, remove the Least Recently Used (LRU) item among them.

**Method Requirements:**
- `put(key, item)`: Adds an item to the cache, discarding the least frequently used item when full. If there’s a tie, remove the least recently accessed among them.
- `get(key)`: Retrieves an item and updates both its frequency and access history.
