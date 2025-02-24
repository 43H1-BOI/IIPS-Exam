# **Internal 1st 2K24-25**
---
## **Q1. What is a Stack?**

A **stack** is a linear data structure that follows the **LIFO** (Last In, First Out) principle.  
- This means the last element added to the stack is the first one to be removed.  
- Think of it like a stack of plates where you can only add or remove plates from the top.  

#### **Key Operations of a Stack**:
1. **Push**: Add an element to the top of the stack.  
2. **Pop**: Remove the top element from the stack.  
3. **Peek/Top**: View the top element without removing it.  
4. **IsEmpty**: Check if the stack is empty.  

---

#### **Uses of Stack**

1. **Expression Evaluation and Conversion**:  
   - Convert infix expressions to postfix or prefix.
   - Evaluate postfix expressions.

2. **Backtracking**:  
   - Used in algorithms like **Depth-First Search (DFS)**.
   - Helps in undo operations in text editors.

3. **Function Call Management**:  
   - Recursion uses a stack to keep track of function calls.

4. **Parenthesis Matching**:  
   - Used to check if parentheses/brackets in an expression are balanced.

5. **Data Reversal**:  
   - Reverse a string or data using a stack.

6. **Syntax Parsing**:  
   - Compilers use stacks to parse expressions, syntax trees, and code generation.

---

#### **Example**

**Stack Operations**:
1. Push elements: `[10, 20, 30]` → Stack becomes `[10, 20, 30]`.  
2. Pop element: Remove `30` → Stack becomes `[10, 20]`.  
3. Peek/Top: Top element is `20`.






# **Internal 2nd 2K24-25**
---
## **Q5. Construct a binary tree from the given In-order and Pre-order traversal sequences.**
In-order sequence: D, B, E, A, F, C
<br>Pre-order sequence: A, B, D, E, C, F


#### Constructed Tree:
```
       A
      / \
     B   C
    / \  /
   D   E F
```
---

# **End Sem 2K23-24**
## Q2. b) Define :
### **Dequeue (Double-Ended Queue):**
A **Dequeue** is a data structure in which elements can be added or removed from **both ends** (front and rear). It combines the features of both stacks and queues.

#### Characteristics:
- Insertion and deletion can be performed at both ends.
- There are two main types of deques:
  1. **Input-restricted deque**: Insertions are allowed at one end, but deletions can be performed at both ends.
  2. **Output-restricted deque**: Deletions are allowed at one end, but insertions can be performed at both ends.

#### Applications:
- Managing tasks in a sliding window.
- Keeping track of the recent history in applications like text editors.

---

### **Priority Queue:**
A **Priority Queue** is an abstract data structure where each element has a priority assigned to it. Elements with **higher priority** are served before those with lower priority. If two elements have the same priority, their order of service depends on the implementation (e.g., FIFO for equal priorities).

#### Characteristics:
- Can be implemented using data structures like heaps, arrays, or linked lists.
- Common operations:
  - **Insert**: Add an element to the queue.
  - **Extract/Remove Max/Min**: Remove the element with the highest or lowest priority.
  - **Peek**: View the element with the highest or lowest priority without removing it.

#### Applications:
- CPU scheduling in operating systems.
- Dijkstra’s algorithm for finding the shortest path.
- Event-driven simulations.


---

## Q3. a) **Advantages and Disadvantages of Linked List over Array**

### **Advantages of Linked List:**
1. **Dynamic Size**: 
   - A linked list can grow or shrink dynamically, allowing efficient memory utilization without requiring reallocation or resizing like arrays.
   
2. **Efficient Insertions/Deletions**:
   - Insertions and deletions at any position are more efficient compared to arrays because shifting elements is not required.
   
3. **No Memory Wastage**:
   - Memory is allocated as needed for linked list nodes, avoiding the need to preallocate memory like arrays.
   
4. **Flexible Data Storage**:
   - Elements can be stored in non-contiguous memory locations, making better use of memory fragmentation.

---

### **Disadvantages of Linked List:**
1. **Memory Overhead**:
   - Each node requires additional memory for the pointer/reference to the next node.
   
2. **Sequential Access**:
   - Linked lists require traversal from the head to access elements, making random access inefficient compared to arrays.
   
3. **Complexity**:
   - Implementing and managing linked lists is more complex than arrays, especially when handling edge cases (e.g., empty lists, inserting at the head/tail).
   
4. **Cache Unfriendliness**:
   - Since elements are not stored in contiguous memory, linked lists have poorer cache locality compared to arrays, which can impact performance.

---

## b) **Collision in Hashing**

### **What is Collision?**
- A **collision** occurs in hashing when two different keys are hashed to the same index in a hash table. This is inevitable because the hash function maps a large number of possible keys into a fixed number of indices.

---

### **Collision Handling Techniques:**
1. **Chaining (Separate Chaining)**:
   - Store all elements that hash to the same index in a **linked list** or other structure at that index.
   - Advantages:
     - Easy to implement.
     - Handles a high load factor (number of elements / table size).
   - Disadvantages:
     - Overhead of linked list pointers.
     - May degrade to linear search in the worst case.

2. **Open Addressing**:
   - Instead of using separate structures, collisions are resolved by finding another open slot in the hash table itself.
   - Common methods:
     - **Linear Probing**: Check the next slot sequentially.
     - **Quadratic Probing**: Check slots at increasing intervals (e.g., 1², 2², 3²...).
     - **Double Hashing**: Use a second hash function to determine the step size for probing.
   - Advantages:
     - No additional memory for linked lists.
     - Faster in practice for low load factors.
   - Disadvantages:
     - Performance deteriorates as the table becomes full.
     - Clustering can occur, especially with linear probing.

3. **Perfect Hashing**:
   - Use a secondary hash function designed to eliminate collisions for a fixed set of keys.
   - Suitable for static sets of data where keys are known in advance.

4. **Rehashing**:
   - When the load factor exceeds a threshold, create a new larger hash table and rehash all the elements.
   - Helps avoid excessive collisions by maintaining a low load factor.

5. **Separate Buckets**:
   - Use other structures like balanced trees or dynamic arrays instead of linked lists for chaining. This reduces the impact of high collisions.

---

### **Key Considerations for Collision Handling:**
- **Load Factor**: Keep the load factor low to minimize collisions.
- **Choice of Hash Function**: A good hash function should distribute keys uniformly to reduce collisions.
- **Performance vs. Memory Trade-offs**: Chaining uses more memory but can handle high load factors efficiently, while open addressing is more memory-efficient but struggles with high load factors.
---

## Q5. b) Explan :
### **a) Complete and Connected Graph**

1. **Complete Graph**:  
   - A graph where every pair of vertices is directly connected by an edge.  
   - Example: For 3 vertices \( A, B, C \):  
     - Edges: \( AB, AC, BC \). All possible connections are present.  

2. **Connected Graph**:  
   - A graph where there is at least one path between any two vertices.  
   - Example: If \( A \) is connected to \( B \), and \( B \) is connected to \( C \), then \( A \) and \( C \) are indirectly connected.  
   - **Key Difference**: A connected graph does not require every vertex to have a direct edge, unlike a complete graph.

---

### **b) Strictly and Complete Binary Tree**

1. **Strictly Binary Tree (Full Binary Tree)**:  
   - A binary tree where every non-leaf node has **exactly two children**.  
   - Example:
     ```
         A
       /   \
      B     C
     ```
   - **Note**: Leaf nodes do not have children.

2. **Complete Binary Tree**:  
   - A binary tree where:
     - All levels are fully filled **except the last level**, and
     - All nodes in the last level are as far left as possible.  
   - Example:
```
         A
       /   \
      B     C
     / \
    D   E
```

---

### **c) Max and Min Heap**

1. **Max Heap**:  
   - A binary tree where:  
     - The value of each parent node is **greater than or equal** to its children.  
     - The root node contains the **largest value**.  
   - Example:
     ```
         50
       /    \
      30     20
     ```

2. **Min Heap**:  
   - A binary tree where:  
     - The value of each parent node is **less than or equal** to its children.  
     - The root node contains the **smallest value**.  
   - Example:
     ```
         10
       /    \
      15     30
     ```

---
---
---

