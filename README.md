# Breadth-First Search (BFS) in Python

## 📌 Overview

This project demonstrates the implementation of the **Breadth-First Search (BFS)** algorithm in Python using a graph represented as an adjacency list.

BFS is a fundamental graph traversal algorithm used to explore nodes level by level. It is commonly used to find the **shortest path** in an unweighted graph.

---

## 🚀 Features

* Traverses graph using BFS technique
* Finds the shortest path between two nodes
* Uses:

  * `deque` for efficient queue operations
  * `set` for tracking visited nodes
  * `parent dictionary` for path reconstruction
* Prints step-by-step traversal

---

## 🧠 How It Works

1. Start from the initial node
2. Visit all its neighbors
3. Move to the next level of nodes
4. Continue until the goal node is found
5. Reconstruct the path using parent pointers

---

## 🗂️ Graph Representation

```python
graph = {
    'A': ['B', 'C'],
    'B': ['A', 'D', 'E'],
    'C': ['A', 'F'],
    'D': ['B'],
    'E': ['B', 'F'],
    'F': ['C', 'E']
}
```

---

## 💻 Code Implementation

```python
from collections import deque 

def bfs(graph, start, goal): 
    visited = set([start]) 
    queue = deque([start]) 
    parent = {start: None} 
    
    print(f"Starting BFS from '{start}' to find goal '{goal}'\n") 
    
    while queue: 
        current = queue.popleft() 
        print(f"Visiting node: {current}") 
        
        if current == goal: 
            print(f"\nGoal '{goal}' found!") 
            
            path = [] 
            node = current 
            while node is not None: 
                path.append(node) 
                node = parent[node] 
            
            path.reverse() 
            return path 
        
        for neighbor in graph[current]: 
            if neighbor not in visited: 
                visited.add(neighbor) 
                parent[neighbor] = current 
                queue.append(neighbor) 
                print(f" Discovered new node: {neighbor}") 
    
    return None
```

---

## ▶️ Example Usage

```python
result_path = bfs(graph, 'A', 'F')
print("\nBFS Path from A to F:", " -> ".join(result_path))
```

---

## 📊 Sample Output

```
Starting BFS from 'A' to find goal 'F'

Visiting node: A
 Discovered new node: B
 Discovered new node: C

Visiting node: B
 Discovered new node: D
 Discovered new node: E

Visiting node: C
 Discovered new node: F

Visiting node: D
Visiting node: E
Visiting node: F

Goal 'F' found!

BFS Path from A to F: A -> C -> F
```

---

## 🎯 Applications of BFS

* Shortest path in unweighted graphs
* Social network analysis
* Web crawling
* GPS navigation systems
* AI search algorithms

---

## 🛠️ Requirements

* Python 3.x

---

## 📌 Conclusion

This project provides a simple and clear implementation of BFS, helping understand how graph traversal and shortest path finding works in real-world scenarios.

---

## 🙌 Author

Developed as part of learning Data Structures & Algorithms.
