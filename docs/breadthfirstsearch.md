## Breadth First Search

```python
class Vertex:
    def __init__(self,label):
        self.label=label
        self.d=math.inf
        self.color='WHITE'
        self.adj_sets=[]
        self.parent=None
    def addAdj(self,v):
        if v not in self.adj_sets:
            self.adj_sets.append(v)

import math
class Graph:
    def __init__(self):
        self.vertices=[]
    def addVertex(self,u):
        if u not in self.vertices:
            self.vertices.append(u)
    def addEdge(self,u,v):
        self.addVertex(v)
        self.addVertex(u)
        u.addAdj(v)
        v.addAdj(u)
R=Vertex('R')
S=Vertex('S')
T=Vertex('T')
U=Vertex('U')
V=Vertex('V')
W=Vertex('W')
X=Vertex('X')
Y=Vertex('Y')

G=Graph()

G.addEdge(R,Y)
G.addEdge(R,S)
G.addEdge(S,W)
G.addEdge(W,T)
G.addEdge(W,X)
G.addEdge(T,U)
G.addEdge(T,X)
G.addEdge(X,U)
G.addEdge(X,Y)
G.addEdge(U,Y)
from collections import deque
def BFS(G,s):
    s.color='GRAY'
    s.d=0
    queue=deque([s])
    while queue:
        u=queue.pop()
        for v in u.adj_sets:
            if v.color=='WHITE':
                 v.color='GRAY'
                 v.d=u.d+1
                 v.parent=u
                 queue.append(v)
        u.color='BLACK'
BFS(G,S)
for vertex in G.vertices:
    print(vertex.label)
    print(vertex.d)

```
