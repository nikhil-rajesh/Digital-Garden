# Artificial Intelligence

## Search Strategies

A strategy is defined by picking the **order of node expansion**

Strategies are evaluated along the following dimensions: 

* **Completeness** - ****does it always find a solution if one exists? 
* **Optimality** - does it always find a least-cost solution? 
* **Time Complexity** - number of nodes generated/expanded 
* **Space Complexity** - maximum number of nodes in memory 
* **Systematicity** - does it visit each state at most once?

Time and space complexity are measured in terms of 

* _**b**_ - maximum branching factor of the search tree
* _**d**_ - depth of the least-cost solution 
* _**m**_ - maximum depth of the state space \(may be ∞\)

## Uninformed Search Strategies

{% hint style="info" %}
[https://www.javatpoint.com/ai-uninformed-search-algorithms](https://www.javatpoint.com/ai-uninformed-search-algorithms)
{% endhint %}

* Depth First Search
* Breadth First Search 
* Uniform Cost Search
* Depth Limited Search
* Iterative Deepening Search

### Depth First Search

The algorithm starts at the root node \(selecting some arbitrary node as the root node in the case of a graph\) and explores as far as possible along each branch before backtracking.

* Complete - **No**
* Time Complexity - **O\(bᵐ\)**
* Space Complexity - **O\(bm\)**

### Breadth First Search \(Shortest First\)

The algorithm starts at the tree root and explores all nodes at the present depth prior to moving on to the nodes at the next depth level.

* Complete - **Yes \(If b is finite\)**
* Time Complexity - **O\(bᵈ\)**
* Space Complexity - **O\(bᵈ\)**
* Optimal - **Yes \(If step cost = 1\)**

### Uniform Cost Search \(Cheapest First\)

The alogrithm visits the node that has the least cost to visit. Once visited, its children are added to the priority queue

* Complete - **Yes \(If b is finite\)**
* Time Complexity - **O\(b ^ \(C\*/e\)\)**
  * **C\*** - Optimal Time
  * **e** - Lowest cost
* Space Complexity - **O\(b ^ \(C\*/e\)\)**
* Optimal - **Yes**

