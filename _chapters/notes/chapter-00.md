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
- insert(index, element): Inserts an element at a given index.
    - **O(1)** time complexity.

- append(element): Adds an element at the end of the array.
    - **O(1)** time complexity.

- pop(): Removes and returns the last element of the array.
    - **O(1)** time complexity.

            arr = [2, 3, 4]
            arr.append(5) # arr = [2, 3, 4, 5]
            arr.insert(1, 6) # arr = [2, 6, 3, 4, 5]
            arr.pop() # arr = [2, 6, 3, 4]

## Sort, reverse and len functions in an array
Other important functions are: sort, reverse, and len.
- sort(): Sorts the array in ascending order.
    - **O(n log n)** time complexity.

- reverse(): Reverses the array.
    - **O(n log n)** time complexity.

- : Returns the length of the array.
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
- add(item): Adds a single element to the set.
    - **O(1)** time complexity.

- update(anotherSet): Merges items from a list, tuple, or another set.
    - **O(m)** time complexity where m is the quantity of elements to iterate.

- remove(item): Removes the item. Raises a KeyError if it doesn't exist.
    - **O(1)** time complexity.

- discard(item): Removes the item. Does nothing if the item is missing..
    - **O(1)** time complexity.

- clear(): Removes all elements, leaving the set empty.
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

# Dictionaries (dict)

It allows you to store data as mapped associations, making it incredibly easy and fast to look up 
values using a specific key rather than an index number.

**Some properties**:

- **Ordered**: Starting in Python 3.7, dictionaries maintain the insertion order of their keys.
- **Unique Keys**: Keys must be unique. If you assign a value to an existing key, it overwrites the old value.
- **Hashable Keys Only**: Dictionary keys must be of an immutable data type (like strings, numbers, or tuples). Values, however, can be absolutely anything (lists, sets, or even other dictionaries).

## Creating a dictionary
You can create a dictionary using curly braces {} with key: value pairs, or by using the built-in dict() constructor.

    # Creating a dictionary with elements
    user = {
        "name": "Alice",
        "age": 28,
        "city": "New York"
    }
    print(user)  # Output: {'name': 'Alice', 'age': 28, 'city': 'New York'}

    # Creating an empty dictionary
    empty_dict = {} 
    another_empty = dict()

## Accessing and Modifying Data

You can read, add, or change data using square brackets [] or the .get() method.

    user = {"name": "Alice", "age": 28}

    # Accessing values
    print(user["name"])       # Output: Alice
    # print(user["email"])    # Throws a KeyError because 'email' doesn't exist

    # Safe accessing with .get() (Returns None or a default value instead of crashing)
    print(user.get("email"))         # Output: None
    print(user.get("email", "N/A"))  # Output: N/A

    # Adding or Updating a value
    user["age"] = 29          # Updates existing key 'age'
    user["email"] = "alice@example.com"  # Adds a new key-value pair

## Common Methods

Python dictionaries come with built-in methods to extract data or clean up the structure:

- keys(): Returns a view object of all keys in the dictionary.
- values():	Returns a view object of all values.
- items(): Returns a view object of tuples containing (key, value).
- pop(key): Removes the specified key and returns its value.
- update(other_dict): Updates the dictionary with pairs from another dictionary.
- .clear(): Deletes all items from the dictionary.

## Dictionaries using defaultdict

A defaultdict is a subclass of Python's built-in dictionary found in the collections module.
It overrides one method and adds a writable instance variable to automatically provide a default value for a missing key, preventing KeyError exceptions.
When you pass a lambda function to defaultdict, you can customize exactly what that default value should be.

    from collections import defaultdict

    # The lambda defines the default value when a key doesn't exist yet
    my_dict = defaultdict(lambda: "Default Value")

### Basic Example: Custom Default Values

Standard dictionaries crash with a KeyError if you look up a key that isn't there. defaultdict automatically creates the key and assigns the value returned by your lambda.

    from collections import defaultdict

    # Create a dictionary where any missing key defaults to 0
    score_board = defaultdict(lambda: 0)

    # We can immediately manipulate keys that haven't been defined yet
    score_board["player_one"] += 10 

    print(score_board["player_one"])  # Output: 10
    print(score_board["new_player"])  # Output: 0 (Automatically created!)

Using defaultdict(lambda) removes the need to constantly use if key not in dict: or dict.setdefault(key, default). This makes your loop bodies cleaner, faster, and highly readable.

# Heaps 
A heap in Python is a specialized tree-based data structure that satisfies the heap property: in a min-heap, the parent node is always less than or equal to its children, meaning **the smallest element is always at the root (index 0)**.

## Importing and Core Operations

To use heaps, you must import the heapq module. All operations modify a standard Python list in-place.

    import heapq

    # Create a regular list
    numbers = [5, 1, 3, 9, 2]

    # Turn the list into a heap in-place -> O(N) time
    heapq.heapify(numbers)
    print(numbers)  # Output: [1, 2, 3, 9, 5] (Index 0 is always the smallest)

    # Push a new element -> O(log N) time
    heapq.heappush(numbers, 0)

    # Pop and return the smallest element -> O(log N) time
    smallest = heapq.heappop(numbers)
    print(smallest)  # Output: 0
    print(numbers[0]) # Output: 1 (The new smallest element)

## Common heapq Methods
- heapify(list): Transforms a list into a heap in-place.
    - **O(n) time complexity**. The heapify() function uses an optimized bottom-up algorithm known as Floyd's Backshift (or Sift-Down) algorithm.
- heappush(heap, item): Pushes a value onto the heap while maintaining the heap property.
    - **O(log n) time complexity**.  
- heappop(heap): Pops and returns the smallest item from the heap.
    - **O(log n) time complexity**.  
- heappushpop(heap, item): Pushes a new item, then pops and returns the smallest item. More efficient than calling them separately.
    - **O(log n) time complexity**.  
- nlargest(n, iterable): Returns a list with the n largest elements from the dataset.
    - **O(n log n) time complexity**.  
- nsmallest(n, iterable): Returns a list with the n smallest elements from the dataset.
    - **O(n log n) time complexity**.  

## How to implement a Max-Heap

Because heapq only provides a min-heap, if you need a max-heap (where index 0 is always the largest element), the standard Python convention is to invert the signs of the numbers when pushing and popping.

# Tuples 

A tuple is an ordered, immutable collection of elements. Unlike lists (which use square brackets []), tuples are defined using parentheses ().
The definitive feature of a tuple is its immutability—once created, you cannot add, remove, or modify its values.

## Creating a Tuple

You can create a tuple with multiple elements, an empty tuple, or even omit parentheses entirely (known as tuple packing).

    # Creating a standard tuple
    coordinates = (40.7128, -74.0060)

    # The single-element trap (You MUST include a trailing comma!)
    # If you write just (5), Python treats it as the integer 5 inside math parentheses.
    single_element = (5,) 

    # Creating a tuple without parentheses (Tuple Packing)
    my_tuple = 1, 2, 3  # Python automatically packages this into (1, 2, 3)

## Core Characteristics

• **Immutable**: Attempting to assign a new value to an index (e.g., coordinates[0] = 50) will throw a TypeError. This prevents accidental data corruption.
• **Ordered & Indexed**: Elements maintain a fixed position. You can read them using integer indices (coordinates[0]) and perform standard slicing operations.
• **Hashable Keys**: Because tuples are immutable, they can be used as keys in a dictionary or as elements within a set (set)—something that is completely impossible with lists.

## Built-in Methods

Because tuples cannot be altered, they only possess two native methods:

Method	Example	Description
- count(value)
    - my_tuple.count(5):Returns the total number of times a value appears.
- index(value) 
    - my_tuple.index("A"): Returns the first index position of the value (raises ValueError if missing).

## Why Use a Tuple Instead of a List?

- **Performance**: Tuples are faster and allocation-optimized under the hood. Python allocates a single memory block for them, whereas lists require extra dynamic overallocation space.
- **Data Integrity**: Perfect for guarding structural constants (e.g., configurations, days of the week, geolocation data).
- **Function Returns**: When a function returns multiple values separated by commas (return x, y), Python is secretly packaging and returning them as a single tuple.























