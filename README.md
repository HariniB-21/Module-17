# Ex. No: 17A - Generate a Graph for a Given Fixed Degree Sequence

## AIM:
To write a Python program to generate a graph for a given **fixed degree sequence**.

## ALGORITHM:

**Step 1**: Start the program.

**Step 2**: Check if the sum of the degree sequence is even.  
> (A necessary condition for the sequence to be graphical.)

- If not even, print an error message and exit the program.

**Step 3**: Use the **Havel-Hakimi algorithm** to determine whether a simple graph can be constructed from the sequence, and to generate the graph.

**Step 4**: If the graph is successfully created, **visualize it** using a graph drawing function (e.g., `networkx.draw()`).

**Step 5**: End the program.

## PYTHON PROGRAM

```python
"""
Reg no: 212222020008
Name : Harini B
A Python program to demonstrate the adjacency
list representation of the graph
"""

# A class to represent the adjacency list of the node


class AdjNode:
	def __init__(self, data):
		self.vertex = data
		self.next = None


# A class to represent a graph. A graph
# is the list of the adjacency lists.
# Size of the array will be the no. of the
# vertices "V"
class Graph:
	def __init__(self, vertices):
		self.V = vertices
		self.graph = [None] * self.V

	# Function to add an edge in an undirected graph
	def add_edge(self, src, dest):
		# Adding the node to the source node
		node = AdjNode(dest)
		node.next = self.graph[src]
		self.graph[src] = node

		# Adding the source node to the destination as
		# it is the undirected graph
		node = AdjNode(src)
		node.next = self.graph[dest]
		self.graph[dest] = node

	
	def print_graph(self):
	    for i in range(self.V):
	        print("Adjacency list of vertex {}\n head".format(i),end=" ")
	        temp=self.graph[i]
	        while temp:
	            print("-> {}".format(temp.vertex),end=" ")
	            temp=temp.next
	        print("\n")




# Driver program to the above graph class
if __name__ == "__main__":
	V = 5
	graph = Graph(V)
	graph.add_edge(0, 1)
	graph.add_edge(0, 4)
	graph.add_edge(1, 2)
	graph.add_edge(1, 3)
	graph.add_edge(1, 4)
	graph.add_edge(2, 3)
	graph.add_edge(3, 4)

	graph.print_graph()

```

## OUTPUT
![image](https://github.com/user-attachments/assets/7a7bed5e-e524-44b9-8098-cfb0afb6b782)


## RESULT
Thus, a Python program to demonstrate the adjacency list representation of the given graph is executed successfully.


# Ex. No: 17B - BFS Traversal from a Given Source Vertex

## AIM:
To write a Python program to **print BFS traversal** from a given source vertex.

## ALGORITHM:

**Step 1**: Start the program.

**Step 2**: Create a graph using **adjacency list representation**.

**Step 3**: Add edges between vertices using the `addEdge()` method.

**Step 4**: Implement the `BFS()` function:
- Initialize all vertices as **not visited**.
- Use a **queue** to track vertices for traversal.
- Mark the **starting vertex** as visited and enqueue it.
- Dequeue a vertex, process it, and enqueue all its **adjacent unvisited vertices** while marking them as visited.

**Step 5**: Input the **starting vertex** and perform BFS traversal from it.

**Step 6**: Print the vertices in **BFS order**.

**Step 7**: End the program.

---
## PYTHON PROGRAM

```python

Reg no: 212222020008
Name : Harini B

# Python3 Program to print BFS traversal
# from a given source vertex. BFS(int s)
# traverses vertices reachable from s.
from collections import defaultdict

# This class represents a directed graph
# using adjacency list representation
class Graph:

	# Constructor
	def __init__(self):

		# default dictionary to store graph
		self.graph = defaultdict(list)

	# function to add an edge to graph
	def addEdge(self,u,v):
		self.graph[u].append(v)

	# Function to print a BFS of graph
	def BFS(self, s):

		# Mark all the vertices as not visited
		visited = [False] * (max(self.graph) + 1)

		# Create a queue for BFS
		queue = []

		# Mark the source node as
		# visited and enqueue it
		queue.append(s)
		visited[s] = True

		while queue:
		    
		    s=queue.pop(0)
		    print(s,end=" ")
		    
		    for i in self.graph[s]:
		        if visited[i]==False:
		            queue.append(i)
		            visited[i]=True
# Create a graph given in
# the above diagram
n=int(input())
g = Graph()
g.addEdge(0, 1)
g.addEdge(0, 2)
g.addEdge(1, 2)
g.addEdge(2, 0)
g.addEdge(2, 3)
g.addEdge(3, 3)

print ("Following is Breadth First Traversal"
				" (starting from vertex {})".format(n))
g.BFS(n)

```

## OUTPUT
![image](https://github.com/user-attachments/assets/f39b2841-dd78-4a1f-b66f-d1cc821c4e47)


## RESULT
Thus, the Python program to print BFS traversal from a given source vertex is verified and executed successfully.

# Ex. No: 17C - DFS Traversal from a Given Source Vertex

## AIM:
To write a Python program to **print DFS traversal** from a given source vertex.

## ALGORITHM:

**Step 1**: Start the program.

**Step 2**: Create a graph using **adjacency list representation**.

**Step 3**: Add edges between vertices using the `addEdge()` method.

**Step 4**: Implement the `DFSUtil()` function to **recursively visit** and print each unvisited vertex:
- Mark the current vertex as **visited**.
- Recursively call `DFSUtil` for each **unvisited adjacent vertex**.

**Step 5**: In the `DFS()` function:
- Initialize an empty set for visited vertices.
- Call `DFSUtil()` starting from the given vertex.

**Step 6**: Input the **starting vertex** and perform DFS traversal.

**Step 7**: Print the vertices in **DFS order**.

**Step 8**: End the program.

## PYTHON PROGRAM

```python

Reg no: 212222020008
Name : Harini B

# Python3 program to print DFS traversal
# from a given graph
from collections import defaultdict

# This class represents a directed graph using
# adjacency list representation


class Graph:

	# Constructor
	def __init__(self):

		# default dictionary to store graph
		self.graph = defaultdict(list)

	# function to add an edge to graph
	def addEdge(self, u, v):
		self.graph[u].append(v)

	# A function used by DFS
	def DFSUtil(self, v, visited):

		# Mark the current node as visited
		# and print it
		visited.add(v)
		print(v,end=" ")
		for neighbour in self.graph[v]:
		    if neighbour not in visited:
		        self.DFSUtil(neighbour,visited)
		
		
		
		#.....
		
		
		# Code here 
		
		
		
		#....
		
		
	# The function to do DFS traversal. It uses
	# recursive DFSUtil()
	def DFS(self, v):

		# Create a set to store visited vertices
		visited = set()

		# Call the recursive helper function
		# to print DFS traversal
		self.DFSUtil(v, visited)

# Driver code


# Create a graph given
# in the above diagram
n=int(input())
g = Graph()
g.addEdge(0, 1)
g.addEdge(0, 2)
g.addEdge(1, 2)
g.addEdge(2, 0)
g.addEdge(2, 3)
g.addEdge(3, 3)

print("Following is DFS from (starting from vertex {})".format(n))
g.DFS(n)

```

## OUTPUT
![image](https://github.com/user-attachments/assets/8be590d4-b9af-4dbc-b809-44f037fff842)


## RESULT
Thus, the Python program to print DFS traversal from a given source vertex is executed successfully.

# Ex. No: 17D - Topological Sorting of a DAG

## AIM:
To write a Python program to **print topological sorting** of a **Directed Acyclic Graph (DAG)**.

## ALGORITHM:

**Step 1**: Create a graph and add edges to represent relationships between nodes.

**Step 2**: Use a `visited` set to keep track of visited nodes and a **stack** (or list) to record the **order of nodes** after processing.

**Step 3**: Perform **DFS** for each unvisited node:
- Explore all its neighbors.
- Recursively apply DFS to each unvisited adjacent node.
- After all neighbors are visited, **push the current node onto the stack**.

**Step 4**: After DFS is complete for all nodes, the stack will contain nodes in **reverse order of their completion time**.

**Step 5**: Print the stack in **reverse** to get the **topological order**.

---

## PYTHON PROGRAM

```python
Reg no: 212222020008
Name : Harini B

# A Python3 program to print topological sorting of a DAG
def addEdge(u, v):
	global adj
	adj[u].append(v)

# The function to do DFS() and stores departure time
# of all vertex
def DFS(v):
	global visited, departure, time
	visited[v] = 1
	for i in adj[v]:
		if visited[i] == 0:
			DFS(i)
	departure[time] = v
	time += 1

# The function to do Topological Sort. It uses DFS().
def topologicalSort():
    for i in range(V):
        if (visited[i]==0):
            DFS(i)
    for i in range(V-1,-1,-1):
        print(departure[i],end=" ")
if __name__ == '__main__':

	# Create a graph given in the above diagram
	V,time, adj, visited, departure = 6, 0, [[] for i in range(7)], [0 for i in range(7)],[-1 for i in range(7)]
	addEdge(5, 2)
	addEdge(5, 0)
	addEdge(4, 0)
	addEdge(4, 1)
	addEdge(2, 3)
	addEdge(3, 1)

	print("Topological Sort of the given graph is")
	topologicalSort()

```

## OUTPUT
![image](https://github.com/user-attachments/assets/967eeefd-9aac-41e6-8c6b-eeec0d87e1a8)


## RESULT
Thus, the Python program to print topological sorting of a Directed Acyclic Graph (DAG) is executed successfully.


# Ex. No: 17E - Adjacency List Representation of a Graph

## AIM:
To write a Python program to demonstrate the **adjacency list representation** of the given graph.

---

## ALGORITHM:

**Step 1**: Start the program.

**Step 2**: Define a class `AdjNode` to create a node for each adjacent vertex:
- Store the **vertex number**.
- Store the **link to the next adjacent node**.

**Step 3**: Define a class `Graph` to create the graph using adjacency lists:
- Initialize the **number of vertices**.
- Create a **list (array)** of size `V`, where each element is initially `None`.

**Step 4**: Define a method `add_edge(src, dest)` to:
- Add `dest` to the adjacency list of `src`.
- Add `src` to the adjacency list of `dest` (for **undirected graphs**).

**Step 5**: Define a method `print_graph()` to:
- Traverse the adjacency list of each vertex.
- Print the **vertex** and its **adjacent nodes**.

**Step 6**: In the main program:
- Create a `Graph` object with `V` vertices.
- Call `add_edge()` for all desired edges.
- Call `print_graph()` to display the adjacency list.

**Step 7**: End the program.

---


## PYTHON PROGRAM

```python
Reg no: 212222020008
Name : Harini B

"""
A Python program to demonstrate the adjacency
list representation of the graph
"""

# A class to represent the adjacency list of the node


class AdjNode:
	def __init__(self, data):
		self.vertex = data
		self.next = None


# A class to represent a graph. A graph
# is the list of the adjacency lists.
# Size of the array will be the no. of the
# vertices "V"
class Graph:
	def __init__(self, vertices):
		self.V = vertices
		self.graph = [None] * self.V

	# Function to add an edge in an undirected graph
	def add_edge(self, src, dest):
		# Adding the node to the source node
		node = AdjNode(dest)
		node.next = self.graph[src]
		self.graph[src] = node

		# Adding the source node to the destination as
		# it is the undirected graph
		node = AdjNode(src)
		node.next = self.graph[dest]
		self.graph[dest] = node

	
	def print_graph(self):
	    for i in range(self.V):
	        print("Adjacency list of vertex {}\n head".format(i),end=" ")
	        temp=self.graph[i]
	        while temp:
	            print("-> {}".format(temp.vertex),end=" ")
	            temp=temp.next
	        print("\n")



# Driver program to the above graph class
if __name__ == "__main__":
	V = 5
	graph = Graph(V)
	graph.add_edge(0, 1)
	graph.add_edge(0, 4)
	graph.add_edge(1, 2)
	graph.add_edge(1, 3)
	graph.add_edge(1, 4)
	graph.add_edge(2, 3)
	graph.add_edge(3, 4)

	graph.print_graph()

```

## OUTPUT
![image](https://github.com/user-attachments/assets/6ad6e70e-964b-4783-989b-95eed16c4160)


## RESULT
Thus , the Python program for demonstrating the adjacency list representation of the given graph is verified and executed successfully.

