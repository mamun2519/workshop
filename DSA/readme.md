# Data Structures and Algorithm with Javascript

## Expand The DSA Full Form

DSA stands for Data structures & Algorithms. These are two different terms.

**Data Structures:**The storage where you can store data.

In **computer science**, a **data structure** is like those storage items — it’s a way of organizing and storing data so you can use it effectively.

Imagine you’re organizing your house. You have different storage items like:

- A drawer for socks
- A bookshelf for books
- A shoe rack for shoes
- A fridge for food
  Each of these helps you store and access things efficiently.

**Algorithms:** The procedures, the operations we need to work on the data.

In programming, an algorithm is a set of instructions to manipulate data and solve a problem.

Now, imagine you’re baking a cake. You follow a step-by-step recipe:

1. Get ingredients
2. Mix them
3. Bake for 30 minutes
4. Serve
   That recipe is an algorithm — a sequence of steps to solve a problem or accomplish a task. It requires data to process and these data is stored inside one or many data structures.

## Why Algorithm always comes with Data Structures

Data Structures without Algorithm is a sealed treasure that we can not open. Algorithm without having a data structure is just a set of instructions, we don’t need to worry about them. You almost never need one without the other.

### Common Data Structures

We are surrounded by data structures

List of Common Structures:

- Array
- Linked List
- Stack
- Queue
- Hash Table / Hash Map
- Set
- Tree
- Heap
- Trie
- Graph

## Common Operations

Operation Meaning

- Insert => Add new data into the structure or memory
- Delete => Remove data from a specific location
- Update => Modify existing data
- Search/Find => Locate specific data based on a value or key
- Read/Access => Retrieve data from a location without modifying it
- Traverse => Visit all elements in a structured way (e.g., one by one, top to bottom)
- Sort => Rearrange data based on a rule (ascending, alphabetical, etc.)
- Transform => Convert data into another format/structure
- Merge => Combine two or more data collections into one
- Split => Divide a data collection into parts
- Map => Apply a function to every element (common in functional programming)
- Filter => Select elements based on a condition
- Aggregate => Compute a summary (sum, average, count, etc.)

## How to choose the correct data structure

Why do we need different data structures and algorithms?

Analogy: Untidy Expensive Room vs Tidy Cheap Room

We need to perform different operations to achieve different things. Some data structures are good at some operations while other data structures are good at some other operations. Based on the operations we need to decide which data structures will perform better. Sometimes, we need to use multiple data structures on same data for different operations.

But how can we know which data structures will perform better on which data structures? How do we measure? What is the metric?

The following two programs are doing the same thing, sorting an array. Between these two program which one will perform better?

## Asymptotic Analysis

Asymptotic analysis is a method used to describe the limiting behavior of a function or algorithm as its input size increases towards infinity. It's particularly useful in computer science for understanding the efficiency and scalability of algorithms by focusing on how their performance changes with large inputs, ignoring constant factors and low-level details

### Key Concepts:

- Focus on Growth Rate: Asymptotic analysis focuses on the rate at which an algorithm's resource usage (e.g., time or space) grows as the input size increases.
- Asymptotic Notations: It employs mathematical notations like Big O, Big Omega, and Big Theta to express these growth rates.
- Ignoring Constants: Constant factors and specific input sizes are often ignored because they become less relevant as the input grows large.
- Scalability: Asymptotic analysis helps determine how well an algorithm will perform with larger datasets or inputs, providing insights into its scalability.
- Performance Comparison: It allows for the comparison of different algorithms' efficiencies by looking at their asymptotic growth rates.

## Notations:

- Big (O) - Upper Bound: In the worst case scenario the algorithm will take at most this much time. Used the most in algorithm analysis. Ex. You were looking for a book and found it at the last.
- Big (Ω) - Lower Bound: In the best case scenario the algorithm will take this much time. Ex. You found the desired book at the first attempt.
- Big (Θ) - Tight Bound: Describe the exact growth rate. The algorithm takes this much time in all cases. Used when the upper and lower bounds are the same.

## The domination Rules

When combining multiple time complexities:

- Take the term with the highest growth rate.
- It dominates the rest as input size n grows large.
  This is called the “dominant term” rule in asymptotic analysis.

Because Big-O is about growth trends, not exact counts.

For large n:

- n³ grows much faster than n², which grows faster than n log n, etc.
- So n³ + n² + log n is O(n³)
  This is like adding pennies to millions - the pennies become negligible.

## Space Complexity

Space complexity includes:

- Input storage
- Temporary variables
- Function call stack
- Data structures used

### Input Storage

- This refers to the space needed to store the input data to the algorithm.
- Even though input size is not "created" by the algorithm, we usually include it when analyzing space complexity.
- For example, if you're given an array of n integers, the input storage is O(n).
  ⚠️ Some analyses might exclude input size when focusing only on additional space used, but by default it's considered.

### Temporary Variables

- These are variables created during the execution of an algorithm to store intermediate values.
- Examples: counters, accumulators, loop variables, etc.
- These usually take constant space, so they contribute O(1) unless you're using large or dynamic data types.

### Function Call Stack

- Each time a function is called, especially recursively, memory is allocated for:
  - parameters
  - return address
  - local variables
- Recursive algorithms can have significant space complexity due to deep call stacks.
- For example, a recursive function that calls itself n times contributes O(n) space.

### Data Structures Used

- If your algorithm uses extra data structures (arrays, hash maps, trees, etc.), their size affects space complexity.
- For instance, an algorithm that creates a new array of size n uses O(n) additional space.
- Even if the input size is small, using large auxiliary structures increases the overall space requirement.

## Type of Data Structures

A data structure is a way to organize, store, and access data efficiently so we can perform operations like searching, insertion, deletion, and modification. There are two different ways we can organize our data:

- Linear
- Non Linear

Linear Data Structures: In linear data structures, elements are arranged sequentially — one after another. Each element has a unique predecessor and successor (except the first and last).

- Array => Elements stored in contiguous memory locations, indexed.
- Linked List => Nodes connected via pointers, flexible in size.
- Stack => Follows LIFO (Last In First Out) principle.
- Queue => Follows FIFO (First In First Out) principle.

Non-Linear Data Structures: In non-linear data structures, data is not arranged sequentially. Instead, it forms hierarchies or interconnected networks. Each element can be connected to multiple elements.

- Tree => Hierarchical structure with parent-child relationships.
- Graph => Collection of nodes (vertices) connected by edges (can be directional or bidirectional).
- Heap => Specialized tree with ordering properties.
- Trie => Tree-like structure used for string searching.

## Array

An array is a linear data structure that stores elements in a contiguous block of memory. Each element in the array is identified by an index, which allows direct access to any element using that index.

An array is a linear data structure that stores elements in a contiguous block of memory. Each element in the array is identified by an index, which allows direct access to any element using that index.

### Core Characteristics

- Fixed Indexing: Every element has a numeric index starting from 0.
- Contiguous Memory: All elements are stored next to each other in memory.
- Same Data Type (in low-level languages): Classic arrays hold elements of the same type (e.g., all integers).
- Efficient Access: Accessing any element is done in constant time → O(1).

| Operation       | Description                                      | Time Complexity | Notes                                                             |
| --------------- | ------------------------------------------------ | --------------- | ----------------------------------------------------------------- |
| Access          | Get an element by its index: `arr[i]`            | O(1)            | Direct memory access via index. Super fast.                       |
| Update          | Replace an element at a specific index           | O(1)            | Similar to access — instant overwrite.                            |
| Insert (End)    | Add element at the end: `arr.push(val)`          | O(1)\*          | Amortized O(1); resizing may cost O(n) when capacity is exceeded. |
| Insert (Start)  | Add element at the beginning: `arr.unshift(val)` | O(n)            | All elements must shift one index right.                          |
| Insert (Middle) | `arr.splice(i, 0, val)`                          | O(n)            | Everything after index i shifts.                                  |
| Delete (End)    | Remove last element: `arr.pop()`                 | O(1)            | Just removes the last element.                                    |
| Delete (Start)  | Remove first: `arr.shift()`                      | O(n)            | All elements shift left by one.                                   |
| Delete (Middle) | `arr.splice(i, 1)`                               | O(n)            | Elements after index i shift left.                                |
| Find (by value) | `arr.indexOf(val)` or `arr.includes(val)`        | O(n)            | Linear search. No built-in hashing/index map.                     |

## Hash Table

A Hash Table (also called Hash Map in many programming languages) is a data structure used to store key-value pairs. It allows you to insert, delete, and retrieve data very quickly—typically in constant time: O(1) on average.
Think of it like a real-world dictionary:

- You look up a word (the key)
- And get its meaning (the value)
  The book (hash table) organizes things so you can find any word quickly
