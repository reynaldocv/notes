---
layout: home
chapter: "Python Programming Tips"
course: "Python Programming Tips"
permalink: "notes-00/"
---

# All Libraries used in this note

All tips and tricks mentioned in this note are based on the following libraries. 
    
    from heapq import heappush, heappop, heapify
    from collections import defaultdict
    from functools import cache
    from math import inf, gcd


# Arrays 
## Insert, append and pop elements in an array
In array, we have two important functions: insert, append and pop. 
- insert: Inserts an element at a given index.
    - **O(1)** time complexity.

- append: Adds an element at the end of the array.
    - **O(1)** time complexity.

- pop: Removes and returns the last element of the array.
    - **O(1)** time complexity.

            arr = [2, 3, 4]
            arr.append(5) # arr = [2, 3, 4, 5]
            arr.insert(1, 6) # arr = [2, 6, 3, 4, 5]
            arr.pop() # arr = [2, 6, 3, 4]

## Sort, reverse and len functions in an array
Other important functions are: sort, reverse, and len.
- sort: Sorts the array in ascending order.
    - **O(n log n)** time complexity.

- reverse: Reverses the array.
    - **O(n log n)** time complexity.

- len: Returns the length of the array.
    - **O(1)** time complexity.

            arr = [2, 3, 4]
            arr.sort() # arr = [2, 3, 4]
            arr.reverse() # arr = [4, 3, 2]
            len(arr) # returns 3

## Sorting an array based on a specific condition

We can use the sort function with a key parameter to sort the array based on a specific condition using a lambda function. 
- For example, we can sort an array of tuples based on the second element of each tuple.

        arr = [(1, 2), (3, 1), (2, 3)]
        arr.sort(key=lambda x: x[1]) 
        # arr = [(3, 1), (1, 2), (2, 3)]

- For example, we can sort an array of tuples based on the second element of each tuple, then sort in descending order based on the first element of each tuple.

        arr = [(1, 2), (3, 3), (1, 3), (2, 1)]
        arr.sort(key=lambda x: (x[1], -x[0])) 
        # arr = [(3, 3), (1, 3), (1, 2), (2, 1)]

## Sorted function
    
Doing sort without altering the array can be done using the sorted function. 

    arr = [2, 3, 4]
    sorted_arr = sorted(arr) 
    # sorted_arr = [2, 3, 4], arr = [2, 3, 4].

Both sort function and sorted function can be used to sort an array based on a specific condition using a lambda function. Both have **O(n log n)** time complexity.

## Enumerate function

To list the index and value of each element in an array, we can use the enumerate function. 

    arr = [2, 3, 4]
    for (ith, value) in enumerate(arr):
        print(ith, value)
    # Output:
    # 0 2
    # 1 3
    # 2 4

To list all elements in an array since respetive start 

    arr = [2, 3, 4]
    for (ith, value) in enumerate(arr, 2):
        print(ith, value)
    # Output:
    # 2 2
    # 3 3
    # 4 4

# Sets 

A set is an unordered, mutable collection of unique elements. It is the ideal data structure when you need to avoid duplicate items or perform mathematical set operations like unions and intersections.

**Some properties**:

- **No Duplicates**: If you add a duplicate item, Python silently ignores it.
- **Unordered & Unindexed**: Elements have no fixed position. You cannot access items using an index (e.g., fruits[0] raises a TypeError).
- **Hashable Elements Only**: While the set itself is mutable (you can add/remove items), the elements inside it must be immutable/hashable (like strings, numbers, or tuples). You cannot put a list or a dict inside a set.

## Creating a Set

You can create a set using curly braces {} or the built-in set() function.

    # Creating a set with elements
    fruits = {"apple", "banana", "orange", "apple"}
    print(fruits)  
    # Output: {'orange', 'apple', 'banana'} 
    (Duplicates are removed, order changes)

    # Creating an empty set (You MUST use set())
    # Using empty curly braces {} creates an empty dictionary, not a set!
    empty_set = set() 

## Add, update, remove, discard and clear

In sets, we have the following important functions:  
- add: Adds a single element to the set.
    - **O(1)** time complexity.

- update: Merges items from a list, tuple, or another set.
    - **O(m)** time complexity where m is the quantity of elements to iterate.

- remove: Removes the item. Raises a KeyError if it doesn't exist.
    - **O(1)** time complexity.

- discard: Removes the item. Does nothing if the item is missing..
    - **O(1)** time complexity.

- clear: Removes all elements, leaving the set empty.
    - **O(n)** time complexity.

## Mathematical Set Operations

Sets make crossing data incredibly easy using either operators or equivalent methods:

    A = {1, 2, 3, 4}
    B = {3, 4, 5, 6}

    # Union: All unique elements from both sets
    print(A | B)          # {1, 2, 3, 4, 5, 6}
    print(A.union(B))

    # Intersection: Only elements present in both sets
    print(A & B)          # {3, 4}
    print(A.intersection(B))

    # Difference: Elements in A that are NOT in B
    print(A - B)          # {1, 2}
    print(A.difference(B))

    # Symmetric Difference: Elements in either set, but NOT in both
    print(A ^ B)          # {1, 2, 5, 6}
    print(A.symmetric_difference(B))

## Performance Tip: Fast Lookups

Checking if an item exists inside a set using the in operator is highly optimized. Because sets use a hash table under the hood, lookups take O(1) constant time on average. This is significantly faster than searching through a large list (O(n) time).

    allowed_users = {"alice", "bob", "charlie"}
    if "alice" in allowed_users:
        print("Access granted")

















