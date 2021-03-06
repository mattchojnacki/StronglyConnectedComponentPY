### Strongly Connected Component
* 8 May

## Python lib:
* sys
* ast
* networkx
* matplotlib.pyplot
* PyQt4

<img src="/img/graph.png" height="688 " width="681" />

## How to start?
* Download all lib using pip install
* $ python gui.py
* input type edges and connections between them like json:
```
[
  (1, 0),
  (0, 2),
  (2, 1),
  (0, 3),
  (3, 4)
]

```


## Algorythm Strongly Connected Component

```
#This class represents a directed graph using adjacency list representation
class Graph:

    def __init__(self,vertices):

        self.V= vertices #No. of vertices
        self.graph = defaultdict(list) # default dictionary to store graph

    # function to add an edge to graph
    def addEdge(self,u,v):
        self.graph[u].append(v)

    # A function used by DFS
    def DFSUtil(self,v,visited):
        # Mark the current node as visited and print it
        visited[v]= True
        print v,
        valueList.append(v)
        #Recur for all the vertices adjacent to this vertex
        for i in self.graph[v]:
            if visited[i]==False:
                self.DFSUtil(i,visited)


    def fillOrder(self,v,visited, stack):
        # Mark the current node as visited
        visited[v]= True
        #Recur for all the vertices adjacent to this vertex
        for i in self.graph[v]:
            if visited[i]==False:
                self.fillOrder(i, visited, stack)
        stack = stack.append(v)


    # Function that returns reverse (or transpose) of this graph
    def getTranspose(self):
        g = Graph(self.V)

        # Recur for all the vertices adjacent to this vertex
        for i in self.graph:
            for j in self.graph[i]:
                g.addEdge(j,i)
        return g

    def printSCCs(self):

        stack = []
        # Mark all the vertices as not visited (For first DFS)
        visited =[False]*(self.V)
        # Fill vertices in stack according to their finishing
        # times
        for i in range(self.V):
            if visited[i]==False:
                self.fillOrder(i, visited, stack)

        # Create a reversed graph
        gr = self.getTranspose()

        # Mark all the vertices as not visited (For second DFS)
        visited =[False]*(self.V)

        # Now process all vertices in order defined by Stack
        while stack:
            i = stack.pop()
            if visited[i]==False:
                if i != 0: valueList.append("->")
                gr.DFSUtil(i, visited)
                print""
        return valueList

```
