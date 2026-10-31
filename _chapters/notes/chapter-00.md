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
    for (ith, value) in enumerate(arr, 1):
        print(ith, value)
    # Output:
    # 0 2
    # 1 3
    # 2 4




















