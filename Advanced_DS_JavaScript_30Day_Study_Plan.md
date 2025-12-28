# Advanced Data Structures - 30-Day Study Plan (JavaScript)

_For experienced JavaScript engineers preparing for senior-level interviews_

---

## 30-Day Study Plan Overview

| Day | Data Structure / Topic       | Focus Area                                           |
| --- | ---------------------------- | ---------------------------------------------------- |
| 1   | Advanced Arrays              | Sliding Window, Two Pointers, Prefix Sums            |
| 2   | Advanced Arrays              | Kadane's, Dutch National Flag, Subarray Patterns     |
| 3   | Hash Maps & Frequency        | Frequency Counting, Mapping Patterns, Anagrams       |
| 4   | Stack                        | Basic Stack, Expression Evaluation, Backtracking     |
| 5   | Monotonic Stack              | Next Greater/Smaller Element, Histogram Problems     |
| 6   | Queue & Deque                | Circular Queue, Deque, Sliding Window Maximum        |
| 7   | Linked Lists                 | Fast/Slow Pointers, Reversal, Cycle Detection        |
| 8   | Linked Lists                 | Advanced Patterns, Merge, Reorder, Palindrome        |
| 9   | Binary Trees                 | Traversals (Iterative), Level Order, Views           |
| 10  | Binary Trees                 | Path Problems, LCA, Serialization                    |
| 11  | Binary Search Trees          | BST Properties, Validation, Operations               |
| 12  | BST Advanced                 | Iterator, Successor/Predecessor, Recovery            |
| 13  | Heaps & Priority Queue       | Min/Max Heap, Kth Element, Merge K                   |
| 14  | Heaps Advanced               | Running Median, Top K Frequent, Custom Comparators   |
| 15  | Tries                        | Basic Trie, Word Search, Autocomplete                |
| 16  | Tries Advanced               | Word Dictionary, Stream Processing, Prefix Matching  |
| 17  | **Review Week 1-16**         | Practice mixed problems, identify weak areas         |
| 18  | Graphs - BFS/DFS             | Traversal Templates, Connected Components, Islands   |
| 19  | Graphs - Shortest Path       | Dijkstra, Bellman-Ford, Floyd-Warshall               |
| 20  | Graphs - Advanced            | Topological Sort, Cycle Detection, Bipartite         |
| 21  | Union Find                   | Disjoint Set, Path Compression, Union by Rank        |
| 22  | Segment Tree                 | Range Query, Range Update, Lazy Propagation          |
| 23  | Fenwick Tree (BIT)           | Point Update, Range Sum, Inversion Count             |
| 24  | LRU / LFU Cache              | Cache Design, Doubly Linked List + Hash Map          |
| 25  | Bit Manipulation             | Bitwise Operations, XOR Tricks, Subsets              |
| 26  | Interval Data Structures     | Merge Intervals, Insert, Overlap Detection           |
| 27  | Advanced Patterns            | Sweep Line, Coordinate Compression, Difference Array |
| 28  | Mixed Problem Solving        | Combine multiple data structures                     |
| 29  | **Review & Mock Interviews** | Time-boxed problem solving                           |
| 30  | **Final Review**             | Revisit hardest problems, implementation speed       |

---

## 1. Advanced Arrays & Sliding Window

### Conceptual Overview

**Problem Solved**: Efficiently process contiguous subarrays or windows of data without recomputing from scratch.

**When Used**:

- Finding optimal subarray/substring with constraints
- Processing streaming data
- Range queries with fixed or variable window sizes

**Complexity Table**:

| Operation                 | Time                   | Space        |
| ------------------------- | ---------------------- | ------------ |
| Sliding Window (fixed)    | O(n)                   | O(1) to O(k) |
| Sliding Window (variable) | O(n)                   | O(1) to O(k) |
| Two Pointers              | O(n)                   | O(1)         |
| Prefix Sum                | O(n) build, O(1) query | O(n)         |

### Core Variants

1. **Fixed-Size Sliding Window**: Window size is constant
2. **Variable-Size Sliding Window**: Expand/contract based on condition
3. **Two Pointers (Same Direction)**: Both move left to right
4. **Two Pointers (Opposite Direction)**: One from start, one from end
5. **Prefix Sum**: Precompute cumulative sums for range queries

**Trade-offs**:

- Fixed window: Simple but limited to fixed constraints
- Variable window: More flexible but requires careful boundary management
- Prefix sum: O(n) space but enables O(1) range queries

### Important Algorithms

#### Kadane's Algorithm

- **Key Idea**: Find maximum sum subarray by tracking current and global max
- **Complexity**: O(n) time, O(1) space
- **JS Consideration**: Handle negative numbers, empty arrays

#### Dutch National Flag (3-way partitioning)

- **Key Idea**: Partition array into three sections using two pointers
- **Complexity**: O(n) time, O(1) space
- **JS Consideration**: In-place swap without temp variable: `[arr[i], arr[j]] = [arr[j], arr[i]]`

#### Sliding Window Maximum

- **Key Idea**: Use deque to maintain decreasing order of elements
- **Complexity**: O(n) time, O(k) space
- **JS Consideration**: No native deque, use array with shift() carefully or implement

### Must-Know Patterns

1. **Shrinkable Window**: Expand right, shrink left when invalid

   - Signal: "minimum/maximum window that satisfies..."

2. **Non-shrinkable Window**: Only expand, track max size

   - Signal: "longest subarray/substring with at most..."

3. **Counting with Hash Map**: Track frequency in current window

   - Signal: "contains all characters", "at most K distinct"

4. **Prefix Sum for Subarray Sum**: Use map to store sum → index

   - Signal: "subarray sum equals K", "continuous subarray"

5. **Two Pointers for Sorted Arrays**: Opposite direction movement
   - Signal: Array is sorted, find pair/triplet with target sum

### Top Interview Questions

**Easy**:

1. Maximum Average Subarray I (fixed window)
2. Contains Duplicate II (sliding window with set)
3. Move Zeroes (two pointers)
4. Remove Duplicates from Sorted Array (two pointers)

**Medium**: 5. Longest Substring Without Repeating Characters 6. Minimum Size Subarray Sum 7. Fruit Into Baskets (at most 2 types) 8. Subarray Product Less Than K 9. Maximum Number of Vowels in Substring (fixed window) 10. Longest Repeating Character Replacement 11. Subarrays with K Different Integers 12. Minimum Window Substring

**Hard**: 13. Sliding Window Maximum 14. Substring with Concatenation of All Words 15. Minimum Number of K Consecutive Bit Flips

### Implementation Checklist

- [ ] Fixed-size sliding window template
- [ ] Variable-size sliding window (expandable/shrinkable)
- [ ] Two pointers (same direction and opposite)
- [ ] Prefix sum array construction and query
- [ ] Kadane's algorithm from memory
- [ ] Dutch National Flag algorithm

---

## 2. Hash Maps & Frequency Techniques

### Conceptual Overview

**Problem Solved**: Achieve O(1) average-case lookup, insertion, and deletion; count frequencies; map relationships.

**When Used**:

- Frequency counting and analysis
- Detecting duplicates or unique elements
- Mapping indices, characters, or patterns
- Implementing caches

**Complexity Table**:

| Operation | Average Time | Worst Time | Space |
| --------- | ------------ | ---------- | ----- |
| Insert    | O(1)         | O(n)       | O(n)  |
| Lookup    | O(1)         | O(n)       | O(n)  |
| Delete    | O(1)         | O(n)       | O(n)  |
| Iteration | O(n)         | O(n)       | -     |

### Core Variants

1. **Map**: Key-value pairs, maintains insertion order (since ES6)
2. **Object**: Similar but keys coerced to strings
3. **Set**: Unique values only
4. **WeakMap/WeakSet**: Keys are objects, allow garbage collection

**Trade-offs**:

- Map vs Object: Map allows any key type, better for frequent add/delete
- Set vs Array: Set guarantees uniqueness, O(1) has() vs O(n) includes()
- WeakMap: No iteration, but doesn't prevent GC

### Important Algorithms

#### Frequency Counter Pattern

- **Key Idea**: Build frequency map, then process by frequency
- **Complexity**: O(n) time, O(n) space
- **JS Consideration**: `map.get(key) || 0` or `map.set(key, (map.get(key) || 0) + 1)`

#### Anagram Grouping

- **Key Idea**: Sort string or use character count as hash key
- **Complexity**: O(n _ k log k) for sort, O(n _ k) for count
- **JS Consideration**: Array as key requires serialization: `JSON.stringify(count)`

#### Two Sum Pattern

- **Key Idea**: Store complements or indices while iterating
- **Complexity**: O(n) time, O(n) space
- **JS Consideration**: Map preserves insertion order for iteration

### Must-Know Patterns

1. **Complement Lookup**: Store seen elements, check for target - current

   - Signal: "find pair that sums to", "two elements"

2. **Index Mapping**: Map value → indices for quick lookup

   - Signal: "find indices of", "positions where"

3. **Frequency Map Then Sort**: Count frequencies, sort by frequency

   - Signal: "top K frequent", "sort by frequency"

4. **Rolling Hash for Substrings**: Hash current window state

   - Signal: "find all anagrams", "grouping substrings"

5. **Prefix Sum + Hash Map**: Store cumulative sum → count/index
   - Signal: "subarray sum equals K", "divisible by K"

### Top Interview Questions

**Easy**:

1. Two Sum
2. Valid Anagram
3. Contains Duplicate
4. Majority Element

**Medium**: 5. Group Anagrams 6. Top K Frequent Elements 7. Subarray Sum Equals K 8. Longest Consecutive Sequence 9. Find All Anagrams in a String 10. 4Sum II 11. Continuous Subarray Sum 12. Pairs of Songs With Total Durations Divisible by 60

**Hard**: 13. Substring with Concatenation of All Words 14. First Missing Positive 15. Longest Substring with At Most K Distinct Characters

### Implementation Checklist

- [ ] Map: insert, lookup, delete, iterate
- [ ] Set: add, has, delete operations
- [ ] Frequency counter from array
- [ ] Anagram detection (sorted and character count methods)
- [ ] Two Sum and variants using Map
- [ ] Group elements by custom hash function

---

## 3. Stack

### Conceptual Overview

**Problem Solved**: LIFO (Last In First Out) access pattern for backtracking, parsing, and maintaining order.

**When Used**:

- Expression evaluation and parsing
- Backtracking and recursion simulation
- Matching pairs (parentheses, tags)
- Undo/redo operations

**Complexity Table**:

| Operation | Time | Space |
| --------- | ---- | ----- |
| Push      | O(1) | O(n)  |
| Pop       | O(1) | -     |
| Peek/Top  | O(1) | -     |
| Search    | O(n) | -     |

### Core Variants

1. **Array-based Stack**: Use array with push/pop
2. **Linked List Stack**: Node-based for dynamic size
3. **Min/Max Stack**: Track minimum/maximum alongside values
4. **Stack with Increment**: Support incrementing bottom k elements

**Trade-offs**:

- Array: Simple, potential resizing overhead
- Linked list: No resizing, extra memory per node
- Min/Max stack: O(1) min/max retrieval for O(n) extra space

### Important Algorithms

#### Balanced Parentheses

- **Key Idea**: Push opening, pop and match closing brackets
- **Complexity**: O(n) time, O(n) space
- **JS Consideration**: Use object/map for bracket mapping

#### Expression Evaluation (Infix/Postfix)

- **Key Idea**: Operator precedence with two stacks (operands and operators)
- **Complexity**: O(n) time, O(n) space
- **JS Consideration**: Handle operator precedence with helper function

#### Next Greater Element (Basic)

- **Key Idea**: Traverse right-to-left, maintain stack of candidates
- **Complexity**: O(n) time, O(n) space
- **JS Consideration**: Result array initialization

### Must-Know Patterns

1. **Matching Pairs**: Stack for opening symbols, pop for closing

   - Signal: "valid parentheses", "balanced brackets"

2. **Backtracking with Stack**: Store states to backtrack

   - Signal: "simplify path", "decode string"

3. **Expression Parsing**: Two stacks or one stack with precedence

   - Signal: "calculator", "evaluate expression"

4. **Min/Max Stack**: Auxiliary stack tracks extrema

   - Signal: "retrieve minimum in O(1)", "stack with min"

5. **Stack for Reversal**: Push all, pop to reverse
   - Signal: "reverse order", "process from back"

### Top Interview Questions

**Easy**:

1. Valid Parentheses
2. Min Stack
3. Implement Stack using Queues
4. Remove All Adjacent Duplicates in String

**Medium**: 5. Evaluate Reverse Polish Notation 6. Decode String 7. Remove K Digits 8. Asteroid Collision 9. Daily Temperatures 10. Basic Calculator II 11. Simplify Path 12. Validate Stack Sequences

**Hard**: 13. Basic Calculator (with parentheses) 14. Longest Valid Parentheses 15. Maximum Frequency Stack

### Implementation Checklist

- [ ] Basic stack using array
- [ ] Stack with linked list
- [ ] Min Stack (track minimum)
- [ ] Valid parentheses checker
- [ ] Postfix expression evaluator
- [ ] Stack-based DFS traversal

---

## 4. Monotonic Stack

### Conceptual Overview

**Problem Solved**: Find next/previous greater or smaller elements efficiently by maintaining elements in monotonic (increasing/decreasing) order.

**When Used**:

- Next/previous greater or smaller element
- Largest rectangle problems
- Stock span problems
- Histogram-based calculations

**Complexity Table**:

| Operation              | Time           | Space |
| ---------------------- | -------------- | ----- |
| Build monotonic stack  | O(n)           | O(n)  |
| Query next greater     | O(1) amortized | -     |
| Query previous smaller | O(1) amortized | -     |

### Core Variants

1. **Monotonic Increasing**: Stack maintains increasing order
2. **Monotonic Decreasing**: Stack maintains decreasing order
3. **Store Indices vs Values**: Indices for position tracking
4. **Circular Array Variant**: Process array twice or use modulo

**Trade-offs**:

- Increasing stack: Finds next smaller element
- Decreasing stack: Finds next greater element
- Indices vs values: Indices enable distance/range calculations

### Important Algorithms

#### Next Greater Element

- **Key Idea**: Traverse right-to-left, pop smaller elements before pushing
- **Complexity**: O(n) time, O(n) space
- **JS Consideration**: Initialize result with -1 or Infinity

#### Largest Rectangle in Histogram

- **Key Idea**: For each bar, find left and right boundaries using monotonic stack
- **Complexity**: O(n) time, O(n) space
- **JS Consideration**: Add sentinel 0 at end to flush stack

#### Stock Span Problem

- **Key Idea**: Count consecutive days with price <= current using stack of indices
- **Complexity**: O(n) time, O(n) space
- **JS Consideration**: Stack stores [price, span] pairs or indices

### Must-Know Patterns

1. **Next Greater/Smaller Element**: Monotonic stack traversal

   - Signal: "next greater", "next warmer", "daily temperatures"

2. **Previous Greater/Smaller Element**: Stack during left-to-right traversal

   - Signal: "previous smaller", "span until"

3. **Range Finding**: Find left and right boundaries for each element

   - Signal: "largest rectangle", "maximum area"

4. **Circular Array**: Traverse array twice using modulo

   - Signal: "circular array", "next greater element II"

5. **Stack with Heights/Values**: Maintain decreasing heights for area calculations
   - Signal: "histogram", "trapping rain water"

### Top Interview Questions

**Easy**:

1. Next Greater Element I
2. Remove Nodes From Linked List (monotonic concept)
3. Final Prices With a Special Discount in a Shop

**Medium**: 4. Daily Temperatures 5. Next Greater Element II (circular) 6. Online Stock Span 7. Largest Rectangle in Histogram 8. Remove Duplicate Letters 9. Sum of Subarray Minimums 10. Car Fleet 11. 132 Pattern

**Hard**: 12. Trapping Rain Water (2D variant) 13. Maximum Rectangle in Binary Matrix 14. Maximal Rectangle 15. Largest Rectangle in Histogram (all variants)

### Implementation Checklist

- [ ] Monotonic increasing stack
- [ ] Monotonic decreasing stack
- [ ] Next greater element template
- [ ] Previous smaller element template
- [ ] Largest rectangle in histogram
- [ ] Circular array with monotonic stack

---

## 5. Queue & Deque

### Conceptual Overview

**Problem Solved**: FIFO (First In First Out) for processing in order; deque allows both ends operations.

**When Used**:

- BFS traversal
- Level-order processing
- Task scheduling
- Sliding window maximum/minimum

**Complexity Table**:

| Operation          | Queue Time | Deque Time | Space |
| ------------------ | ---------- | ---------- | ----- |
| Enqueue/Push Back  | O(1)       | O(1)       | O(n)  |
| Dequeue/Pop Front  | O(1)       | O(1)       | -     |
| Front/Back         | O(1)       | O(1)       | -     |
| Push Front (deque) | -          | O(1)       | -     |

### Core Variants

1. **Simple Queue**: Array with front/rear pointers or shift/push
2. **Circular Queue**: Fixed size with wraparound
3. **Deque (Double-ended Queue)**: Insert/delete from both ends
4. **Priority Queue**: Elements ordered by priority (covered in Heaps)

**Trade-offs**:

- Array shift(): O(n) - avoid for large queues
- Circular queue: Fixed size but O(1) operations
- Deque with array: shift/unshift are O(n) in JS - use linked list or circular buffer

### Important Algorithms

#### Circular Queue Implementation

- **Key Idea**: Use modulo arithmetic for wraparound with fixed-size array
- **Complexity**: O(1) all operations, O(k) space
- **JS Consideration**: Track front, rear, size separately

#### Sliding Window Maximum (using Deque)

- **Key Idea**: Maintain deque of indices in decreasing order of values
- **Complexity**: O(n) time, O(k) space
- **JS Consideration**: Use array, carefully manage both ends

#### BFS Template

- **Key Idea**: Queue for level-order traversal
- **Complexity**: O(V + E) for graphs, O(n) for trees
- **JS Consideration**: Use array with push/shift or implement efficient queue

### Must-Know Patterns

1. **BFS Level Order**: Queue processes nodes level by level

   - Signal: "level order", "shortest path", "minimum depth"

2. **Deque for Window Extrema**: Maintain min/max in sliding window

   - Signal: "sliding window maximum", "minimum in each window"

3. **Circular Queue for Fixed Buffer**: Ring buffer implementation

   - Signal: "design circular queue", "fixed-size buffer"

4. **Queue for State Management**: BFS with state tracking

   - Signal: "minimum moves", "shortest transformation"

5. **Monotonic Deque**: Deque maintains order for window problems
   - Signal: "maximum of all subarrays", "sliding window"

### Top Interview Questions

**Easy**:

1. Implement Stack using Queues
2. Number of Recent Calls
3. Design Circular Queue

**Medium**: 4. Sliding Window Maximum 5. Jump Game VI 6. Shortest Subarray with Sum at Least K 7. Constrained Subsequence Sum 8. Reveal Cards in Increasing Order 9. Dota2 Senate 10. Task Scheduler

**Hard**: 11. Shortest Subarray with Sum at Least K (monotonic deque) 12. Maximum Sum of Distinct Subarrays With Length K 13. Jump Game VII

### Implementation Checklist

- [ ] Queue using array (with shift - understand limitation)
- [ ] Efficient queue using two stacks
- [ ] Circular queue with fixed size
- [ ] Deque operations (both ends)
- [ ] BFS traversal template
- [ ] Sliding window maximum using deque

---

## 6. Linked Lists - Advanced Patterns

### Conceptual Overview

**Problem Solved**: Dynamic size, efficient insertion/deletion, pointer manipulation challenges.

**When Used**:

- Dynamic data with frequent insertions/deletions
- Implementing other data structures (LRU cache)
- Pointer manipulation practice
- When array shifting is expensive

**Complexity Table**:

| Operation      | Singly Linked  | Doubly Linked | Space |
| -------------- | -------------- | ------------- | ----- |
| Access         | O(n)           | O(n)          | O(n)  |
| Insert at head | O(1)           | O(1)          | -     |
| Insert at tail | O(n) or O(1)\* | O(1)          | -     |
| Delete         | O(n)           | O(1)\*\*      | -     |
| Search         | O(n)           | O(n)          | -     |

\*With tail pointer
\*\*If node reference given

### Core Variants

1. **Singly Linked List**: Each node points to next
2. **Doubly Linked List**: Each node points to next and prev
3. **Circular Linked List**: Last node points to first
4. **Skip List**: Multiple levels for faster search

**Trade-offs**:

- Singly: Less memory, can't traverse backward
- Doubly: Can traverse both ways, extra memory per node
- Circular: Useful for round-robin, need careful termination

### Important Algorithms

#### Fast and Slow Pointers (Floyd's Cycle Detection)

- **Key Idea**: Slow moves 1 step, fast moves 2; they meet if cycle exists
- **Complexity**: O(n) time, O(1) space
- **JS Consideration**: Check `fast && fast.next` before moving

#### Reverse Linked List

- **Key Idea**: Iterative with 3 pointers or recursive
- **Complexity**: O(n) time, O(1) space iterative, O(n) recursive
- **JS Consideration**: Careful with `null` checks

#### Merge Two Sorted Lists

- **Key Idea**: Dummy node, compare values, advance pointers
- **Complexity**: O(n + m) time, O(1) space
- **JS Consideration**: Use dummy node to simplify edge cases

### Must-Know Patterns

1. **Fast/Slow Pointers**: Find middle, detect cycle, find cycle start

   - Signal: "middle element", "cycle", "nth from end"

2. **Reversal**: Reverse entire list or portion

   - Signal: "reverse", "swap pairs", "reorder"

3. **Dummy Node**: Simplify edge cases for head changes

   - Signal: "remove elements", "merge", "insert"

4. **Two Pointers with Gap**: N steps ahead for nth from end

   - Signal: "remove nth from end", "rotate list"

5. **Runner Technique**: Multiple pointers at different speeds
   - Signal: "palindrome check", "intersection point"

### Top Interview Questions

**Easy**:

1. Reverse Linked List
2. Merge Two Sorted Lists
3. Linked List Cycle
4. Remove Linked List Elements
5. Middle of the Linked List
6. Palindrome Linked List

**Medium**: 7. Add Two Numbers 8. Remove Nth Node From End 9. Reorder List 10. Swap Nodes in Pairs 11. Rotate List 12. Partition List 13. Sort List 14. Linked List Cycle II 15. Intersection of Two Linked Lists

**Hard**: 16. Reverse Nodes in k-Group 17. Merge k Sorted Lists 18. Copy List with Random Pointer

### Implementation Checklist

- [ ] Singly linked list node and basic operations
- [ ] Doubly linked list node and operations
- [ ] Reverse linked list (iterative and recursive)
- [ ] Fast/slow pointers for cycle detection
- [ ] Find middle element
- [ ] Merge two sorted lists
- [ ] Remove nth from end

---

## 7. Binary Trees - Fundamentals & Traversals

### Conceptual Overview

**Problem Solved**: Hierarchical data representation with fast search, insertion, and ordered traversal (for BST).

**When Used**:

- Hierarchical relationships
- Expression parsing
- File system representation
- Decision trees

**Complexity Table**:

| Operation | Average  | Worst | Space |
| --------- | -------- | ----- | ----- |
| Search    | O(log n) | O(n)  | O(h)  |
| Insert    | O(log n) | O(n)  | O(h)  |
| Delete    | O(log n) | O(n)  | O(h)  |
| Traversal | O(n)     | O(n)  | O(h)  |

h = height of tree

### Core Variants

1. **Full Binary Tree**: Every node has 0 or 2 children
2. **Complete Binary Tree**: All levels filled except possibly last, filled left to right
3. **Perfect Binary Tree**: All internal nodes have 2 children, all leaves at same level
4. **Balanced Binary Tree**: Height difference of subtrees ≤ 1

**Trade-offs**:

- Complete tree: Efficient array representation
- Balanced tree: Guaranteed O(log n) height
- Unbalanced: Can degenerate to O(n) height

### Important Algorithms

#### Inorder Traversal (Iterative)

- **Key Idea**: Stack to simulate recursion, go left, process, go right
- **Complexity**: O(n) time, O(h) space
- **JS Consideration**: While loop with explicit stack

#### Level Order Traversal (BFS)

- **Key Idea**: Queue processes nodes level by level
- **Complexity**: O(n) time, O(w) space (w = max width)
- **JS Consideration**: Track level size for level separation

#### Lowest Common Ancestor

- **Key Idea**: First node where paths to both targets diverge
- **Complexity**: O(n) time, O(h) space
- **JS Consideration**: Recursive with null checks

### Must-Know Patterns

1. **Recursive DFS**: Most tree problems have elegant recursive solutions

   - Signal: "path sum", "symmetric", "depth"

2. **Iterative DFS with Stack**: Convert recursion to iteration

   - Signal: When recursion depth is concern

3. **BFS with Queue**: Level-order processing

   - Signal: "level order", "right side view", "zigzag"

4. **Path Tracking**: Maintain path from root to current

   - Signal: "path sum", "all paths", "root to leaf"

5. **Subtree Problems**: Process subtrees and combine results
   - Signal: "diameter", "maximum path sum", "subtree"

### Top Interview Questions

**Easy**:

1. Maximum Depth of Binary Tree
2. Invert Binary Tree
3. Symmetric Tree
4. Path Sum
5. Binary Tree Paths
6. Same Tree

**Medium**: 7. Binary Tree Inorder Traversal (iterative) 8. Binary Tree Level Order Traversal 9. Zigzag Level Order Traversal 10. Binary Tree Right Side View 11. Validate Binary Search Tree 12. Lowest Common Ancestor of a Binary Tree 13. Kth Smallest Element in a BST 14. Binary Tree Vertical Order Traversal 15. All Nodes Distance K in Binary Tree

**Hard**: 16. Binary Tree Maximum Path Sum 17. Serialize and Deserialize Binary Tree 18. Recover Binary Search Tree

### Implementation Checklist

- [ ] TreeNode class definition
- [ ] Inorder traversal (recursive and iterative)
- [ ] Preorder traversal (recursive and iterative)
- [ ] Postorder traversal (recursive and iterative)
- [ ] Level order traversal (BFS)
- [ ] Height/depth calculation
- [ ] Path sum problems

---

## 8. Binary Search Trees (BST)

### Conceptual Overview

**Problem Solved**: Maintain sorted data with O(log n) search, insert, delete in balanced trees.

**When Used**:

- Sorted data with dynamic insertions/deletions
- Range queries
- Finding kth smallest/largest
- Ordered iteration

**Complexity Table**:

| Operation        | Average (Balanced) | Worst (Skewed) |
| ---------------- | ------------------ | -------------- |
| Search           | O(log n)           | O(n)           |
| Insert           | O(log n)           | O(n)           |
| Delete           | O(log n)           | O(n)           |
| Inorder (sorted) | O(n)               | O(n)           |
| Find min/max     | O(log n)           | O(n)           |

### Core Variants

1. **Standard BST**: Left < root < right property
2. **AVL Tree**: Self-balancing with balance factor tracking
3. **Red-Black Tree**: Self-balancing with color properties
4. **B-Tree**: Multi-way tree for disk storage

**Trade-offs**:

- Standard BST: Simple but can become unbalanced
- AVL: Strictly balanced, more rotations on insert/delete
- Red-Black: Less strictly balanced, fewer rotations

### Important Algorithms

#### BST Validation

- **Key Idea**: Track valid range [min, max] during traversal
- **Complexity**: O(n) time, O(h) space
- **JS Consideration**: Use -Infinity and Infinity for initial bounds

#### BST Insert and Delete

- **Key Idea**: Maintain BST property through pointer manipulation
- **Complexity**: O(h) time, O(h) space (recursive)
- **JS Consideration**: Delete requires finding inorder successor/predecessor

#### Kth Smallest Element

- **Key Idea**: Inorder traversal stops at kth element
- **Complexity**: O(h + k) time, O(h) space
- **JS Consideration**: Use iterative inorder with counter

### Must-Know Patterns

1. **Range Validation**: Pass min/max bounds down recursion

   - Signal: "validate BST", "check if valid"

2. **Inorder for Sorted Access**: Inorder gives sorted sequence

   - Signal: "kth smallest", "sorted array from BST"

3. **BST Iterator**: Inorder traversal with next() interface

   - Signal: "iterator", "next smallest"

4. **Predecessor/Successor**: Navigate BST structure

   - Signal: "inorder successor", "next right node"

5. **BST from Sorted Array**: Binary search to build balanced BST
   - Signal: "convert sorted array", "balanced BST"

### Top Interview Questions

**Easy**:

1. Search in a BST
2. Insert into a BST
3. Minimum Distance Between BST Nodes
4. Two Sum IV - Input is a BST

**Medium**: 5. Validate Binary Search Tree 6. Kth Smallest Element in a BST 7. Delete Node in a BST 8. Convert Sorted Array to Binary Search Tree 9. Inorder Successor in BST 10. Unique Binary Search Trees 11. Binary Search Tree Iterator 12. Recover Binary Search Tree

**Hard**: 13. Count of Smaller Numbers After Self 14. Contains Duplicate III (using TreeSet concept) 15. Maximum Sum BST in Binary Tree

### Implementation Checklist

- [ ] BST search operation
- [ ] BST insert operation
- [ ] BST delete operation
- [ ] BST validation with range check
- [ ] Kth smallest element (iterative)
- [ ] BST iterator with hasNext() and next()
- [ ] Convert sorted array to balanced BST

---

## 9. Heaps & Priority Queue

### Conceptual Overview

**Problem Solved**: Efficiently maintain and retrieve minimum or maximum element; priority-based processing.

**When Used**:

- Finding kth largest/smallest element
- Merging k sorted arrays/lists
- Task scheduling with priorities
- Running median calculation

**Complexity Table**:

| Operation       | Min/Max Heap | Space |
| --------------- | ------------ | ----- |
| Insert          | O(log n)     | O(n)  |
| Extract Min/Max | O(log n)     | -     |
| Peek Min/Max    | O(1)         | -     |
| Heapify         | O(n)         | -     |
| Build Heap      | O(n)         | O(n)  |

### Core Variants

1. **Min Heap**: Parent smaller than children
2. **Max Heap**: Parent larger than children
3. **Binary Heap**: Complete binary tree, array representation
4. **Fibonacci Heap**: Better amortized complexity for some operations
5. **D-ary Heap**: Each node has d children

**Trade-offs**:

- Min vs Max heap: Use min for smallest, max for largest
- Binary heap: Simple, array-based, good cache locality
- Fibonacci heap: Complex but better theoretical bounds

### Important Algorithms

#### Heapify (Bubble Down)

- **Key Idea**: Recursively swap with smaller/larger child to maintain heap property
- **Complexity**: O(log n) time
- **JS Consideration**: Calculate children indices: `2*i+1`, `2*i+2`

#### Build Heap

- **Key Idea**: Heapify from last non-leaf to root
- **Complexity**: O(n) time (not O(n log n)!)
- **JS Consideration**: Start from `Math.floor(n/2) - 1`

#### Heap Sort

- **Key Idea**: Build max heap, repeatedly extract max
- **Complexity**: O(n log n) time, O(1) space
- **JS Consideration**: In-place sorting possible

### Must-Know Patterns

1. **Top K Elements**: Min heap of size k for largest, max heap for smallest

   - Signal: "kth largest", "top k frequent", "k closest"

2. **Merge K Sorted**: Min heap with one element from each list

   - Signal: "merge k sorted arrays", "smallest range"

3. **Two Heaps for Median**: Max heap for left half, min heap for right half

   - Signal: "running median", "median of stream"

4. **Priority Queue for Greedy**: Process by priority order

   - Signal: "minimum cost", "earliest deadline", "scheduling"

5. **Heap for Intervals**: Track overlapping intervals by end time
   - Signal: "minimum meeting rooms", "interval overlap"

### Top Interview Questions

**Easy**:

1. Kth Largest Element in an Array
2. Last Stone Weight
3. Relative Ranks
4. Find K Pairs with Smallest Sums

**Medium**: 5. Top K Frequent Elements 6. K Closest Points to Origin 7. Kth Largest Element in a Stream 8. Reorganize String 9. Task Scheduler 10. Find K Closest Elements 11. Merge k Sorted Lists 12. Find Median from Data Stream

**Hard**: 13. Sliding Window Median 14. IPO (maximize capital) 15. Minimum Cost to Hire K Workers

### Implementation Checklist

- [ ] MinHeap class with insert, extractMin, peek
- [ ] MaxHeap class with insert, extractMax, peek
- [ ] Heapify operation (bubble up and bubble down)
- [ ] Build heap from array in O(n)
- [ ] Kth largest element using heap
- [ ] Merge k sorted lists using heap
- [ ] Running median with two heaps

---

## 10. Tries (Prefix Tree)

### Conceptual Overview

**Problem Solved**: Efficient string prefix operations, autocomplete, spell checking, IP routing.

**When Used**:

- Prefix matching and searching
- Autocomplete systems
- Spell checkers
- Word games (Boggle, Scrabble)
- IP routing tables

**Complexity Table**:

| Operation  | Time | Space                          |
| ---------- | ---- | ------------------------------ |
| Insert     | O(m) | O(m _ n _ alphabet_size) worst |
| Search     | O(m) | -                              |
| StartsWith | O(m) | -                              |
| Delete     | O(m) | -                              |

m = length of word, n = number of words

### Core Variants

1. **Standard Trie**: Each node has children map and isEnd flag
2. **Compressed Trie (Radix Tree)**: Compress single-child chains
3. **Ternary Search Tree**: Space-efficient with 3-way branching
4. **Suffix Trie**: All suffixes of strings inserted

**Trade-offs**:

- Standard trie: Fast but space-intensive
- Radix tree: More space-efficient, slightly slower
- TST: Balance between trie and BST

### Important Algorithms

#### Trie Insert

- **Key Idea**: Create nodes for each character, mark end of word
- **Complexity**: O(m) time where m is word length
- **JS Consideration**: Use `Map` or object for children

#### Trie Search and Prefix Search

- **Key Idea**: Traverse trie following characters
- **Complexity**: O(m) time
- **JS Consideration**: Check `isEnd` for exact match, node existence for prefix

#### Word Search in 2D Grid with Trie

- **Key Idea**: DFS with trie pruning
- **Complexity**: O(rows _ cols _ 4^L) where L is max word length
- **JS Consideration**: Prune trie branches to optimize

### Must-Know Patterns

1. **Prefix Matching**: Check if any word starts with prefix

   - Signal: "starts with", "autocomplete", "prefix search"

2. **Word Dictionary with Wildcards**: Allow '.' to match any character

   - Signal: "word dictionary", "wildcard matching"

3. **Longest Common Prefix**: Build trie, traverse until branching

   - Signal: "longest common prefix", "shared prefix"

4. **Replace Words**: Trie stores roots, replace with shortest root

   - Signal: "replace words", "shortest prefix"

5. **Word Search with Pruning**: Use trie to prune invalid paths early
   - Signal: "word search II", "boggle solver"

### Top Interview Questions

**Easy**:

1. Implement Trie (Prefix Tree)
2. Longest Common Prefix

**Medium**: 3. Design Add and Search Words Data Structure 4. Replace Words 5. Map Sum Pairs 6. Maximum XOR of Two Numbers in an Array 7. Word Search II 8. Design Search Autocomplete System 9. Palindrome Pairs 10. Implement Magic Dictionary

**Hard**: 11. Concatenated Words 12. Stream of Characters 13. Word Squares 14. Prefix and Suffix Search

### Implementation Checklist

- [ ] TrieNode class with children Map and isEnd flag
- [ ] Trie class with insert, search, startsWith methods
- [ ] Delete operation from trie
- [ ] Count words with given prefix
- [ ] Find all words with prefix
- [ ] Word dictionary with wildcard support
- [ ] Autocomplete system

---

## 11. Graphs - BFS & DFS

### Conceptual Overview

**Problem Solved**: Represent and traverse relationships between entities; find paths, connectivity, cycles.

**When Used**:

- Social networks (friends, followers)
- Route finding
- Dependency resolution
- Network flow
- Game states

**Complexity Table**:

| Operation  | Adjacency List | Adjacency Matrix |
| ---------- | -------------- | ---------------- |
| Add vertex | O(1)           | O(V²)            |
| Add edge   | O(1)           | O(1)             |
| Check edge | O(degree)      | O(1)             |
| BFS/DFS    | O(V + E)       | O(V²)            |
| Space      | O(V + E)       | O(V²)            |

### Core Variants

1. **Adjacency List**: Map of vertex → array of neighbors
2. **Adjacency Matrix**: 2D array where matrix[i][j] = edge exists
3. **Edge List**: Array of [u, v, weight] tuples
4. **Directed vs Undirected**: One-way vs bidirectional edges

**Trade-offs**:

- Adjacency list: Space-efficient for sparse graphs
- Adjacency matrix: Fast edge lookup, good for dense graphs
- Directed: Models asymmetric relationships

### Important Algorithms

#### Depth-First Search (DFS)

- **Key Idea**: Go deep before going wide, using stack/recursion
- **Complexity**: O(V + E) time, O(V) space
- **JS Consideration**: Use Set for visited to avoid cycles

#### Breadth-First Search (BFS)

- **Key Idea**: Explore level by level using queue
- **Complexity**: O(V + E) time, O(V) space
- **JS Consideration**: BFS finds shortest path in unweighted graphs

#### Connected Components

- **Key Idea**: Run DFS/BFS from unvisited nodes, count runs
- **Complexity**: O(V + E) time, O(V) space
- **JS Consideration**: Track visited globally across components

### Must-Know Patterns

1. **Island Problems**: DFS/BFS to mark connected components

   - Signal: "number of islands", "connected components", "flood fill"

2. **Shortest Path (Unweighted)**: BFS guarantees shortest path

   - Signal: "shortest path", "minimum moves", "minimum steps"

3. **Cycle Detection**: DFS with recursion stack

   - Signal: "detect cycle", "circular dependency"

4. **Graph Cloning**: DFS/BFS with hash map for visited

   - Signal: "clone graph", "deep copy graph"

5. **Bidirectional BFS**: BFS from both source and target
   - Signal: "word ladder", "minimize transformations"

### Top Interview Questions

**Easy**:

1. Find the Town Judge
2. Find Center of Star Graph
3. Number of Provinces

**Medium**: 4. Number of Islands 5. Clone Graph 6. Course Schedule (cycle detection) 7. Pacific Atlantic Water Flow 8. Surrounded Regions 9. Rotting Oranges (multi-source BFS) 10. Word Ladder 11. 01 Matrix (multi-source BFS) 12. Snakes and Ladders 13. Keys and Rooms

**Hard**: 14. Word Ladder II (shortest path with all paths) 15. Minimum Number of Days to Disconnect Island 16. Swim in Rising Water

### Implementation Checklist

- [ ] Graph representation (adjacency list)
- [ ] DFS recursive traversal
- [ ] DFS iterative with stack
- [ ] BFS iterative with queue
- [ ] Detect cycle in directed graph
- [ ] Detect cycle in undirected graph
- [ ] Count connected components
- [ ] Clone graph

---

## 12. Graphs - Shortest Path & Advanced Algorithms

### Conceptual Overview

**Problem Solved**: Find shortest/cheapest paths in weighted graphs; topological ordering; network flow.

**When Used**:

- Navigation systems
- Network routing
- Task scheduling with dependencies
- Flight/train route planning

**Complexity Table**:

| Algorithm        | Complexity       | Use Case                                |
| ---------------- | ---------------- | --------------------------------------- |
| Dijkstra         | O((V + E) log V) | Single source, non-negative weights     |
| Bellman-Ford     | O(VE)            | Single source, handles negative weights |
| Floyd-Warshall   | O(V³)            | All pairs shortest paths                |
| Topological Sort | O(V + E)         | DAG ordering                            |

### Core Variants

1. **Weighted vs Unweighted**: Edge weights affect shortest path algorithm choice
2. **Directed Acyclic Graph (DAG)**: No cycles, enables topological sort
3. **Negative Weight Edges**: Require Bellman-Ford
4. **All-Pairs Shortest Path**: Floyd-Warshall for dense graphs

**Trade-offs**:

- Dijkstra: Fast but requires non-negative weights
- Bellman-Ford: Handles negative weights, slower
- BFS: Only for unweighted graphs, simplest

### Important Algorithms

#### Dijkstra's Algorithm

- **Key Idea**: Greedy, always expand nearest unvisited vertex
- **Complexity**: O((V + E) log V) with min heap
- **JS Consideration**: Implement min heap or use sorted structure

#### Topological Sort (Kahn's Algorithm)

- **Key Idea**: Process nodes with 0 indegree, reduce neighbors' indegree
- **Complexity**: O(V + E) time, O(V) space
- **JS Consideration**: Use queue for 0-indegree nodes, track indegree array

#### Union-Find (Disjoint Set)

- **Key Idea**: Track connected components with path compression and union by rank
- **Complexity**: O(α(n)) amortized per operation (nearly O(1))
- **JS Consideration**: Array for parent and rank tracking

### Must-Know Patterns

1. **Dijkstra with Min Heap**: Shortest path in weighted graph

   - Signal: "minimum cost", "cheapest flight", "network delay"

2. **Topological Sort for DAG**: Ordering with dependencies

   - Signal: "course schedule", "task ordering", "build order"

3. **Bellman-Ford for Negative Weights**: Detect negative cycles

   - Signal: "negative weights", "arbitrage", "time travel"

4. **Union-Find for Connectivity**: Dynamic connectivity queries

   - Signal: "connected components", "redundant connection", "MST"

5. **Floyd-Warshall for All Pairs**: Distance between all pairs
   - Signal: "shortest path between all", "transitive closure"

### Top Interview Questions

**Easy**:

1. Network Delay Time
2. Find if Path Exists in Graph

**Medium**: 3. Course Schedule (topological sort) 4. Course Schedule II (topological sort with path) 5. Minimum Height Trees 6. Cheapest Flights Within K Stops 7. Path with Maximum Probability 8. Network Delay Time (Dijkstra) 9. All Paths From Source to Target 10. Redundant Connection (Union-Find) 11. Number of Connected Components (Union-Find)

**Hard**: 12. Alien Dictionary (topological sort) 13. Reconstruct Itinerary (Eulerian path) 14. Critical Connections in a Network (Tarjan's) 15. Minimum Cost to Make at Least One Valid Path

### Implementation Checklist

- [ ] Dijkstra's algorithm with min heap
- [ ] Topological sort using Kahn's algorithm (BFS)
- [ ] Topological sort using DFS
- [ ] Union-Find with path compression
- [ ] Union-Find with union by rank
- [ ] Detect cycle using Union-Find
- [ ] Bellman-Ford algorithm
- [ ] Floyd-Warshall algorithm

---

## 13. Segment Tree

### Conceptual Overview

**Problem Solved**: Efficiently answer range queries and updates on arrays (sum, min, max, GCD).

**When Used**:

- Range sum/min/max queries with updates
- Dynamic programming optimizations
- Interval scheduling
- Computational geometry

**Complexity Table**:

| Operation      | Time                           | Space        |
| -------------- | ------------------------------ | ------------ |
| Build          | O(n)                           | O(4n) = O(n) |
| Query (range)  | O(log n)                       | -            |
| Update (point) | O(log n)                       | -            |
| Update (range) | O(log n) with lazy propagation | -            |

### Core Variants

1. **Basic Segment Tree**: Point update, range query
2. **Lazy Propagation**: Deferred range updates
3. **Persistent Segment Tree**: Keep old versions
4. **Dynamic Segment Tree**: Sparse segment tree with coordinate compression

**Trade-offs**:

- Segment tree vs BIT: Segment tree more versatile, BIT simpler
- Lazy propagation: Required for efficient range updates
- Memory: 4n space in worst case

### Important Algorithms

#### Build Segment Tree

- **Key Idea**: Recursively build from leaves, combine results
- **Complexity**: O(n) time, O(n) space
- **JS Consideration**: Array of size 4\*n for safety

#### Range Query

- **Key Idea**: Recursively query left/right, combine results
- **Complexity**: O(log n) time
- **JS Consideration**: Handle complete overlap, no overlap, partial overlap cases

#### Point Update

- **Key Idea**: Update leaf, propagate changes to root
- **Complexity**: O(log n) time
- **JS Consideration**: Update from leaf to root through tree

### Must-Know Patterns

1. **Range Sum Query**: Segment tree for sum aggregation

   - Signal: "range sum with updates", "mutable range sum"

2. **Range Min/Max Query**: Track minimum/maximum in range

   - Signal: "range minimum", "RMQ", "range maximum"

3. **Lazy Propagation**: Defer range updates until needed

   - Signal: "range update", "add value to range"

4. **Count in Range**: Count elements satisfying condition

   - Signal: "count of smaller", "inversions"

5. **Multiple Queries**: Build once, answer many queries
   - Signal: "Q queries", "multiple range queries"

### Top Interview Questions

**Medium**:

1. Range Sum Query - Mutable
2. Count of Smaller Numbers After Self
3. Count of Range Sum
4. Falling Squares
5. My Calendar III
6. The Skyline Problem (can use segment tree)
7. Number of Longest Increasing Subsequence (variant)

**Hard**: 8. Reverse Pairs (merge sort or segment tree) 9. Count of Smaller Numbers After Self 10. Range Module (interval management) 11. Maximum Sum Queries

### Implementation Checklist

- [ ] Build segment tree from array
- [ ] Range sum query
- [ ] Range min query
- [ ] Point update
- [ ] Range update with lazy propagation
- [ ] Query and update template for any associative operation

---

## 14. Fenwick Tree (Binary Indexed Tree)

### Conceptual Overview

**Problem Solved**: Efficiently compute prefix sums and update elements; simpler alternative to segment tree for certain operations.

**When Used**:

- Prefix sum with updates (range sum query)
- Inversion count
- Counting elements in range
- 2D range sum

**Complexity Table**:

| Operation  | Time               | Space |
| ---------- | ------------------ | ----- |
| Build      | O(n log n) or O(n) | O(n)  |
| Prefix Sum | O(log n)           | -     |
| Update     | O(log n)           | -     |
| Range Sum  | O(log n)           | -     |

### Core Variants

1. **Standard BIT**: 1-indexed, prefix sums
2. **2D BIT**: 2D prefix sums
3. **Range Update BIT**: Use difference array technique
4. **Binary Search on BIT**: Find kth smallest

**Trade-offs**:

- BIT vs Segment Tree: BIT is simpler, less memory, but less versatile
- 1-indexed: Simplifies implementation with bit manipulation
- Only works for invertible operations (addition, XOR)

### Important Algorithms

#### Update Element

- **Key Idea**: Update current index and all responsible ancestors
- **Complexity**: O(log n) time
- **JS Consideration**: Use `i += i & -i` to get next responsible index

#### Prefix Sum Query

- **Key Idea**: Sum current and all responsible ancestors
- **Complexity**: O(log n) time
- **JS Consideration**: Use `i -= i & -i` to get previous responsible index

#### Range Sum Query

- **Key Idea**: prefixSum(r) - prefixSum(l-1)
- **Complexity**: O(log n) time
- **JS Consideration**: Handle 0 vs 1-indexed carefully

### Must-Know Patterns

1. **Prefix Sum with Updates**: Classic BIT application

   - Signal: "range sum", "mutable array", "prefix sum"

2. **Inversion Count**: Count pairs where arr[i] > arr[j] and i < j

   - Signal: "inversion count", "reverse pairs"

3. **Count in Range**: Count elements between [l, r]

   - Signal: "count smaller", "count in range"

4. **2D Range Sum**: Extend BIT to 2D

   - Signal: "2D range sum", "matrix sum with updates"

5. **Binary Search on BIT**: Find kth element
   - Signal: "kth smallest with updates"

### Top Interview Questions

**Medium**:

1. Range Sum Query - Mutable
2. Count of Smaller Numbers After Self
3. Reverse Pairs
4. Count of Range Sum

**Hard**: 5. Count of Smaller Numbers After Self (BIT + coordinate compression) 6. Reverse Pairs 7. Create Sorted Array through Instructions 8. Range Sum Query 2D - Mutable (2D BIT)

### Implementation Checklist

- [ ] BIT construction from array
- [ ] Update operation (single point)
- [ ] Prefix sum query
- [ ] Range sum query
- [ ] Find kth smallest element
- [ ] 2D BIT for 2D range sum

---

## 15. LRU / LFU Cache

### Conceptual Overview

**Problem Solved**: Implement caching with eviction policies; maintain order for O(1) access and eviction.

**When Used**:

- Browser caching
- Database query caching
- Operating system page replacement
- API rate limiting

**Complexity Table**:

| Operation | LRU  | LFU  | Space       |
| --------- | ---- | ---- | ----------- |
| Get       | O(1) | O(1) | O(capacity) |
| Put       | O(1) | O(1) | O(capacity) |
| Eviction  | O(1) | O(1) | -           |

### Core Variants

1. **LRU (Least Recently Used)**: Evict least recently accessed
2. **LFU (Least Frequently Used)**: Evict least frequently accessed
3. **FIFO (First In First Out)**: Evict oldest entry
4. **LRU-K**: Consider K most recent accesses

**Trade-offs**:

- LRU: Simple, good for temporal locality
- LFU: Better for frequency-based patterns, more complex
- Combined: LRU with aging for LFU

### Important Algorithms

#### LRU Cache

- **Key Idea**: Doubly linked list + hash map for O(1) get and put
- **Complexity**: O(1) for all operations
- **JS Consideration**: Implement custom doubly linked list nodes

#### LFU Cache

- **Key Idea**: Hash map + min frequency + frequency → doubly linked list map
- **Complexity**: O(1) for all operations
- **JS Consideration**: Track min frequency separately

### Must-Know Patterns

1. **LRU with Doubly Linked List + Map**: Move to front on access

   - Signal: "LRU cache", "least recently used"

2. **LFU with Frequency Buckets**: Group by frequency

   - Signal: "LFU cache", "least frequently used"

3. **Eviction on Capacity**: Remove oldest/least frequent when full

   - Signal: "cache with capacity", "eviction policy"

4. **Update on Access**: Modify recency/frequency on get

   - Signal: "access updates order", "get modifies state"

5. **Hash Map for O(1) Access**: Map key → node
   - Signal: "O(1) get and put", "constant time operations"

### Top Interview Questions

**Medium**:

1. LRU Cache
2. LFU Cache
3. Design In-Memory File System
4. Design Browser History

**Hard**: 5. LFU Cache (complete implementation) 6. All O(1) Data Structure 7. Design Search Autocomplete System (with caching)

### Implementation Checklist

- [ ] Doubly linked list node class
- [ ] LRU cache with get and put operations
- [ ] Move node to front/back operations
- [ ] Remove node from doubly linked list
- [ ] LFU cache with frequency tracking
- [ ] Min frequency maintenance in LFU

---

## 16. Disjoint Set Union (Union-Find)

### Conceptual Overview

**Problem Solved**: Efficiently track and merge disjoint sets; answer connectivity queries.

**When Used**:

- Dynamic connectivity
- Kruskal's MST algorithm
- Cycle detection in undirected graphs
- Percolation problems

**Complexity Table**:

| Operation | Without Optimization | With Path Compression + Union by Rank |
| --------- | -------------------- | ------------------------------------- |
| Find      | O(n)                 | O(α(n)) ≈ O(1)                        |
| Union     | O(n)                 | O(α(n)) ≈ O(1)                        |
| Connected | O(n)                 | O(α(n)) ≈ O(1)                        |

α(n) = inverse Ackermann function (extremely slow-growing, practically constant)

### Core Variants

1. **Quick Find**: Fast find, slow union
2. **Quick Union**: Fast union, slow find
3. **Union by Rank/Size**: Attach smaller tree under larger
4. **Path Compression**: Flatten tree during find

**Trade-offs**:

- Quick find: O(1) find but O(n) union
- Quick union: Unbalanced, can degenerate
- Union by rank + path compression: Nearly O(1) all operations

### Important Algorithms

#### Find with Path Compression

- **Key Idea**: Make all nodes on path point directly to root
- **Complexity**: O(α(n)) amortized
- **JS Consideration**: Recursive or iterative with two passes

#### Union by Rank

- **Key Idea**: Attach tree with smaller rank under tree with larger rank
- **Complexity**: O(α(n)) with path compression
- **JS Consideration**: Track rank array separately

#### Cycle Detection

- **Key Idea**: If both endpoints already in same set, edge creates cycle
- **Complexity**: O(E \* α(V)) for E edges
- **JS Consideration**: Check before union

### Must-Know Patterns

1. **Connected Components**: Count number of disjoint sets

   - Signal: "number of components", "connected parts"

2. **Cycle Detection**: Check if edge connects same component

   - Signal: "redundant connection", "cycle in graph"

3. **Minimum Spanning Tree**: Kruskal's algorithm with Union-Find

   - Signal: "minimum cost to connect", "spanning tree"

4. **Dynamic Connectivity**: Answer if two nodes connected

   - Signal: "are nodes connected", "online connectivity"

5. **Percolation**: Track if top connects to bottom
   - Signal: "percolation", "water flow", "grid connectivity"

### Top Interview Questions

**Easy**:

1. Find if Path Exists in Graph

**Medium**: 2. Number of Connected Components in Undirected Graph 3. Redundant Connection 4. Accounts Merge 5. Most Stones Removed with Same Row or Column 6. Satisfiability of Equality Equations 7. Longest Consecutive Sequence (variant) 8. Number of Islands II (online version)

**Hard**: 9. Smallest String With Swaps 10. Optimize Water Distribution in a Village 11. Minimize Malware Spread 12. Redundant Connection II (directed graph)

### Implementation Checklist

- [ ] Basic Union-Find with parent array
- [ ] Find operation (no optimization)
- [ ] Union operation (no optimization)
- [ ] Find with path compression
- [ ] Union by rank
- [ ] Count number of components
- [ ] Check if two elements connected

---

## 17. Bit Manipulation

### Conceptual Overview

**Problem Solved**: Efficiently perform operations on binary representations; solve subset and state problems.

**When Used**:

- Low-level optimization
- Subset generation
- State representation (bitmask DP)
- Cryptography
- Compression

**Complexity Table**:

| Operation      | Time     | Notes                       |
| -------------- | -------- | --------------------------- |
| AND, OR, XOR   | O(1)     | Single bit operation        |
| Set bit        | O(1)     | `n \| (1 << i)`             |
| Clear bit      | O(1)     | `n & ~(1 << i)`             |
| Check bit      | O(1)     | `(n >> i) & 1`              |
| Count set bits | O(log n) | Brian Kernighan's algorithm |

### Core Variants

1. **Single Number Problems**: XOR properties
2. **Subset Generation**: Iterate through all subsets
3. **Bitmask DP**: Represent state as bitmask
4. **Bit Tricks**: Fast multiplication, division, power of 2 checks

**Trade-offs**:

- Space-efficient state representation
- Often less readable than alternative approaches
- Fast for low-level operations

### Important Algorithms

#### Brian Kernighan's Algorithm (Count Set Bits)

- **Key Idea**: `n & (n-1)` removes rightmost set bit
- **Complexity**: O(number of set bits)
- **JS Consideration**: Works with 32-bit integers in JS

#### XOR for Single Number

- **Key Idea**: a ^ a = 0, a ^ 0 = a
- **Complexity**: O(n) time, O(1) space
- **JS Consideration**: XOR all elements to find unique

#### Generate All Subsets

- **Key Idea**: Iterate from 0 to 2^n - 1, each bit represents inclusion
- **Complexity**: O(2^n \* n)
- **JS Consideration**: Use `(1 << n)` for 2^n

### Must-Know Patterns

1. **XOR for Finding Unique**: Cancel out duplicates

   - Signal: "single number", "appears once", "others appear twice"

2. **Bit Masking for Subsets**: Represent subset as bitmask

   - Signal: "all subsets", "power set", "state representation"

3. **Counting Bits**: Count set bits in number

   - Signal: "hamming weight", "number of 1 bits"

4. **Power of 2 Check**: `n & (n-1) == 0`

   - Signal: "power of two", "check if power"

5. **Swap Without Temp**: `a ^= b; b ^= a; a ^= b`
   - Signal: "swap without temporary variable"

### Top Interview Questions

**Easy**:

1. Single Number
2. Number of 1 Bits
3. Power of Two
4. Reverse Bits
5. Missing Number (XOR approach)
6. Hamming Distance

**Medium**: 7. Single Number II (appears 3 times) 8. Single Number III (two unique numbers) 9. Bitwise AND of Numbers Range 10. Counting Bits 11. Maximum Product of Word Lengths 12. Subsets (bit manipulation approach) 13. Sum of Two Integers (without + operator)

**Hard**: 14. Maximum XOR of Two Numbers in an Array 15. Minimum Number of K Consecutive Bit Flips

### Implementation Checklist

- [ ] Set kth bit
- [ ] Clear kth bit
- [ ] Toggle kth bit
- [ ] Check if kth bit is set
- [ ] Count set bits (Brian Kernighan's)
- [ ] Generate all subsets using bitmask
- [ ] XOR-based single number finder
- [ ] Power of 2 checker

---

## 18. Interval-based Data Structures

### Conceptual Overview

**Problem Solved**: Manage, merge, and query intervals efficiently; handle scheduling and overlap problems.

**When Used**:

- Meeting room scheduling
- Interval merging
- Calendar systems
- Resource allocation
- Range overlap detection

**Complexity Table**:

| Operation       | Sorting Approach | Interval Tree |
| --------------- | ---------------- | ------------- |
| Merge intervals | O(n log n)       | O(n log n)    |
| Insert interval | O(n)             | O(log n)      |
| Query overlaps  | O(n)             | O(log n + k)  |
| Remove interval | O(n)             | O(log n)      |

k = number of overlapping intervals

### Core Variants

1. **Merge Intervals**: Combine overlapping intervals
2. **Interval Tree**: BST-based for interval queries
3. **Sweep Line**: Process events (start/end) in order
4. **Interval Scheduling**: Maximize non-overlapping intervals

**Trade-offs**:

- Sorting: Simple for one-time operations
- Interval tree: Better for dynamic operations
- Sweep line: Efficient for event-based problems

### Important Algorithms

#### Merge Intervals

- **Key Idea**: Sort by start, merge overlapping
- **Complexity**: O(n log n) time, O(n) space
- **JS Consideration**: Sort with custom comparator

#### Insert Interval

- **Key Idea**: Find position, merge with overlapping intervals
- **Complexity**: O(n) time, O(n) space
- **JS Consideration**: Handle three parts: before, overlapping, after

#### Interval Overlap Check

- **Key Idea**: Two intervals overlap if `start1 < end2 && start2 < end1`
- **Complexity**: O(1) for two intervals
- **JS Consideration**: Careful with inclusive vs exclusive ends

### Must-Know Patterns

1. **Sort by Start Time**: Sort intervals, then process

   - Signal: "merge intervals", "non-overlapping intervals"

2. **Greedy Interval Selection**: Choose earliest ending

   - Signal: "minimum rooms", "maximum meetings"

3. **Sweep Line Algorithm**: Process start/end events

   - Signal: "meeting rooms II", "skyline problem"

4. **Insert into Sorted Intervals**: Binary search + merge

   - Signal: "insert interval", "add to calendar"

5. **Interval Overlap Detection**: Check overlap condition
   - Signal: "can attend all meetings", "interval overlap"

### Top Interview Questions

**Easy**:

1. Merge Intervals
2. Meeting Rooms

**Medium**: 3. Insert Interval 4. Meeting Rooms II 5. Non-overlapping Intervals 6. Minimum Number of Arrows to Burst Balloons 7. Interval List Intersections 8. My Calendar I 9. Car Pooling 10. Employee Free Time

**Hard**: 11. My Calendar III 12. The Skyline Problem 13. Data Stream as Disjoint Intervals 14. Range Module

### Implementation Checklist

- [ ] Merge overlapping intervals
- [ ] Insert interval into sorted list
- [ ] Check if two intervals overlap
- [ ] Find minimum meeting rooms (sweep line)
- [ ] Remove covered intervals
- [ ] Interval intersection
- [ ] Sort intervals by start/end time

---

## Weekly Revision Strategy

### Week 1 (Days 1-7): Foundations

**Focus**: Arrays, Hash Maps, Stack, Queue, Linked Lists

**Revision Plan**:

- Day 7: Review Days 1-6
- Solve 2-3 mixed problems combining multiple structures
- Identify weak patterns and redo related problems
- Practice explaining solutions out loud (mock interview style)

**What to Track**:

- Which sliding window variant causes confusion?
- Common mistakes in two-pointer problems
- Stack vs queue selection criteria

### Week 2 (Days 8-14): Trees & Heaps

**Focus**: Binary Trees, BST, Heaps

**Revision Plan**:

- Day 14: Review Days 8-13
- Practice all tree traversals without looking at notes
- Implement heap operations from scratch
- Solve mixed tree problems (combining traversal + path + validation)

**What to Track**:

- Iterative vs recursive trade-offs
- When to use which traversal
- Heap comparator mistakes

### Week 3 (Days 15-21): Advanced Structures

**Focus**: Tries, Graphs, Union-Find

**Revision Plan**:

- Day 17: Review Days 1-16 (major checkpoint)
- Day 21: Review Days 15-21
- Focus on graph problem identification (BFS vs DFS vs Dijkstra)
- Practice drawing graphs and execution traces

**What to Track**:

- Graph representation choice
- Topological sort edge cases
- Union-Find optimization understanding

### Week 4 (Days 22-30): Advanced & Integration

**Focus**: Segment Tree, BIT, Caches, Intervals, Mixed Problems

**Revision Plan**:

- Day 28: Solve problems requiring 2+ data structures
- Day 29: Timed mock interviews (45 min per problem)
- Day 30: Review all implementation checklists

**What to Track**:

- Segment tree vs BIT selection
- Cache implementation details
- Time management in interviews

### Daily Revision Practices

1. **Morning (15 min)**:

   - Review previous day's notes
   - Recite complexity tables from memory
   - Identify patterns without looking at code

2. **Study Session (2-3 hours)**:

   - Follow daily plan
   - Implement from scratch
   - Solve all listed questions (no solutions first)

3. **Evening (30 min)**:
   - Write down what you learned
   - List mistakes made today
   - Plan tomorrow's focus areas

---

## Converting to LeetCode Practice

### Phase 1: Learn Pattern (Days 1-15)

For each data structure:

1. **Implement from scratch** (1 hour)

   - Don't look at solutions
   - Test with edge cases
   - Compare with reference implementation

2. **Solve Easy questions** (2-3 questions)

   - Understand problem → identify pattern → implement
   - Time yourself (15 min per easy question)

3. **Solve Medium questions** (4-5 questions)

   - 25-30 min per question
   - If stuck after 30 min, look at approach (not code)

4. **Solve Hard questions** (1-2 questions)
   - 40-45 min per question
   - Focus on optimization after initial solution

### Phase 2: Mixed Practice (Days 16-25)

1. **Pattern Recognition Drills**:

   - Read problem → identify data structure (30 seconds)
   - Don't solve, just identify
   - Build instinct for pattern matching

2. **Timed Problem Solving**:

   - Set 45-minute timer
   - Solve completely (code + test)
   - If can't finish, analyze why

3. **Company-Tagged Questions**:
   - Pick target companies
   - Filter by data structure + company
   - Solve recent questions (last 6 months)

### Phase 3: Mock Interviews (Days 26-30)

1. **Self-Mock** (Days 26-28):

   - Pick random medium/hard
   - Explain solution out loud
   - Code on whiteboard/paper first
   - Time limit: 45 minutes total

2. **Peer Mock** (Day 29):

   - Exchange interviewer/interviewee roles
   - Follow real interview format
   - Give feedback

3. **Review Session** (Day 30):
   - Revisit hardest problems
   - Identify remaining gaps
   - Create weak areas list for future practice

### LeetCode Tags to Filter By

For each data structure in this plan, use these tags:

- Arrays: `array`, `sliding-window`, `two-pointers`
- Hash Maps: `hash-table`, `hash-map`
- Stack: `stack`, `monotonic-stack`
- Queue: `queue`, `deque`
- Linked Lists: `linked-list`
- Trees: `tree`, `binary-tree`, `binary-search-tree`
- Heaps: `heap`, `priority-queue`
- Tries: `trie`
- Graphs: `graph`, `breadth-first-search`, `depth-first-search`, `topological-sort`, `shortest-path`
- Union-Find: `union-find`, `disjoint-set`
- Segment Tree: `segment-tree`
- BIT: `binary-indexed-tree`
- Bit Manipulation: `bit-manipulation`
- Intervals: `intervals`, `line-sweep`

### Progression Strategy

**Week 1**: 70% Easy, 30% Medium
**Week 2**: 50% Medium, 30% Easy, 20% Hard
**Week 3**: 60% Medium, 40% Hard
**Week 4**: 50% Hard, 30% Medium, 20% Mixed

---

## Common Mistakes JS Engineers Make

### 1. Array Mutation Issues

**Mistake**: Mutating input arrays without realizing

```javascript
// Wrong: mutates input
function process(arr) {
  arr.sort(); // mutates original!
  return arr[0];
}

// Right: create copy if needed
function process(arr) {
  const sorted = [...arr].sort((a, b) => a - b);
  return sorted[0];
}
```

**Fix**: Always clarify if mutation is allowed; use spread or slice for copies.

### 2. Sort Comparator Errors

**Mistake**: Forgetting sort comparator function

```javascript
// Wrong: lexicographic sort
[10, 2, 30].sort(); // [10, 2, 30]

// Right: numeric sort
[10, 2, 30].sort((a, b) => a - b); // [2, 10, 30]
```

**Fix**: Always use comparator for numbers: `(a, b) => a - b` for ascending.

### 3. No Native Deque/Heap

**Mistake**: Using array shift/unshift thinking it's O(1)

```javascript
// Wrong: O(n) operations
while (queue.length) {
  const item = queue.shift(); // O(n) - inefficient!
}
```

**Fix**:

- Implement efficient queue with two stacks or linked list
- Implement min/max heap from scratch
- Or use libraries only if explicitly allowed

### 4. Integer Overflow (Rare but Possible)

**Mistake**: Not considering Number.MAX_SAFE_INTEGER

```javascript
// Can lose precision beyond 2^53 - 1
let large = 9007199254740992; // 2^53
large + 1 === large + 2; // true!
```

**Fix**: Use BigInt for very large integers if needed, or handle as strings.

### 5. Map vs Object Confusion

**Mistake**: Using objects when Map is better

```javascript
// Wrong: keys converted to strings
const obj = {};
obj[1] = "one";
obj["1"] = "ONE"; // overwrites!

// Right: Map preserves key types
const map = new Map();
map.set(1, "one");
map.set("1", "ONE"); // different keys
```

**Fix**: Use Map when keys aren't strings or need iteration order.

### 6. Not Initializing Data Structures Properly

**Mistake**: Forgetting to initialize arrays/maps

```javascript
// Wrong: undefined errors
const freq = {};
for (let num of arr) {
  freq[num]++; // NaN if freq[num] is undefined
}

// Right: initialize with default
const freq = {};
for (let num of arr) {
  freq[num] = (freq[num] || 0) + 1;
}
```

**Fix**: Use `|| 0` pattern or initialize with default values.

### 7. Recursion Stack Overflow

**Mistake**: Deep recursion without considering stack limits

```javascript
// Wrong: can overflow on large n
function factorial(n) {
  return n === 0 ? 1 : n * factorial(n - 1);
}
```

**Fix**: Convert to iteration when recursion depth is large, or use tail call optimization (limited support).

### 8. Modifying Loop Variables

**Mistake**: Changing loop index inside loop body

```javascript
// Wrong: confusing index changes
for (let i = 0; i < arr.length; i++) {
  if (condition) i++; // skip next element - error-prone
}

// Right: use while with explicit control
let i = 0;
while (i < arr.length) {
  if (condition) {
    i += 2;
  } else {
    i++;
  }
}
```

**Fix**: Use while loop for complex iteration control.

### 9. Not Checking for null/undefined in Trees

**Mistake**: Forgetting null checks in tree traversal

```javascript
// Wrong: crashes on null
function traverse(node) {
  traverse(node.left); // crash if node is null!
  traverse(node.right);
}

// Right: check first
function traverse(node) {
  if (!node) return;
  traverse(node.left);
  traverse(node.right);
}
```

**Fix**: Always check `if (!node) return;` at start of tree functions.

### 10. Misunderstanding Pass-by-Value vs Pass-by-Reference

**Mistake**: Expecting primitives to change in functions

```javascript
// Wrong: expecting i to change
function increment(i) {
  i++; // local copy, doesn't affect outside
}
let num = 5;
increment(num);
// num is still 5

// Right: return new value or pass object
function increment(obj) {
  obj.val++; // modifies object
}
```

**Fix**: Remember primitives are pass-by-value, objects/arrays are pass-by-reference.

### 11. Time Complexity Misunderstanding

**Mistake**: Thinking nested loops are always O(n²)

```javascript
// This is O(n), not O(n²)
for (let i = 0; i < n; i++) {
  for (let j = i; j < n; j++) {
    // only processes each element once total
  }
}
```

**Fix**: Analyze actual iterations, not just loop nesting.

### 12. Not Using Built-in Methods Effectively

**Mistake**: Reinventing the wheel

```javascript
// Wrong: manual max finding
let max = arr[0];
for (let num of arr) {
  if (num > max) max = num;
}

// Right: use built-in (if appropriate)
const max = Math.max(...arr);
```

**Fix**: Know when to use built-ins vs implement from scratch (interview context-dependent).

---

## Final Preparation Checklist

### Week Before Interviews

- [ ] Can implement all data structures from "Implementation Checklist" without reference
- [ ] Have solved at least 150 LeetCode problems (50 easy, 75 medium, 25 hard)
- [ ] Can explain time/space complexity for all solutions
- [ ] Have completed at least 5 full mock interviews
- [ ] Can recognize patterns within 1-2 minutes of reading problem
- [ ] Know common edge cases for each data structure

### Day Before Interview

- [ ] Review complexity tables (all data structures)
- [ ] Practice 2-3 easy problems for confidence
- [ ] Review common mistakes list
- [ ] Prepare questions to ask interviewer
- [ ] Ensure development environment ready (if applicable)

### During Interview

- [ ] Clarify problem requirements before coding
- [ ] Discuss approach and get confirmation
- [ ] Think out loud while coding
- [ ] Test with edge cases
- [ ] Analyze time and space complexity
- [ ] Discuss optimization opportunities

---

## Good Luck!

Remember: Advanced data structures are not about memorizing code—they're about understanding when and why to use each structure. Focus on:

1. **Problem → Pattern → Data Structure** recognition
2. **Trade-offs** between different approaches
3. **Implementation details** in JavaScript specifically
4. **Complexity analysis** for every solution

Consistency beats intensity. 2-3 focused hours daily is better than 8-hour weekend crams.

You've got this!
