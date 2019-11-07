### Depth First Search

#### Explanation

Each node will have below properties
1. Color
2. pie(predecessor)
3. d is discovery time
4. f is finishing time

Adjacency list will be used

#### PseudoCode

```python
DFS(G)
    for each vertex u in (G,V)
        u.color = WHITE
        u.pie = NIL
    time = 0
    for each vertex u in (G,V):
        if u.color == WHITE
            DFS_VISIT(G,v)
```

```python
DFS_VISIT(G,u)
    time=time+1
    u.d=time
    u.color=GRAY
    for each v in G.Adj[u]:
        if v.color == WHITE:
            v.pie=u
            DFS_VISIT(G,v)
    u.color=BLACK
    time=time+1
    u.f=time
```


```python
class Vertex:
    def __init__(self,label):
        self.label=label
        self.color='WHITE'
        self.d=0
        self.f=0
        self.adj_sets=[]
        self.parent=None 
    def addAdj(self,v):
        if v not in self.adj_sets:
            self.adj_sets.append(v)
```

#### Undirected Graph


```python
class Graph():
    def __init__(self):
        self.vertices=[]
        self.time=0
    def addVertex(self,v):
        if v not in self.vertices:
            self.vertices.append(v)
    def addEdge(self,u,v):
        self.addVertex(u)
        self.addVertex(v)
        u.addAdj(v)
        v.addAdj(u)
```

#### Directed Graph


```python
class Graph():
    def __init__(self):
        self.vertices=[]
        self.time=0
    def addVertex(self,v):
        if v not in self.vertices:
            self.vertices.append(v)
    def addEdge(self,u,v):
        self.addVertex(u)
        self.addVertex(v)
        u.addAdj(v)
#         v.addAdj(u)
```


```python
def dfs_visit(G,u):
    print('Before')
    print(u.label)
    print(u.d)
    print(u.f)
    G.time=G.time+1
    u.d=G.time
    u.color='GREY'
    for i in u.adj_sets:
        if i.color == 'WHITE':
            i.parent=u
            dfs_visit(G,i)
    u.color='BLACK'
    G.time=G.time+1
    u.f=G.time
    print('After')
    print(u.label)
    print(u.d)
    print(u.f)
```


```python
def dfs(G):
    G.time = 0
    for u in G.vertices:
        if u.color == 'WHITE':
            dfs_visit(G,u)
```


```python
G=Graph()
U=Vertex('U')
V=Vertex('V')
W=Vertex('W')
X=Vertex('X')
Y=Vertex('Y')
Z=Vertex('Z')
```


```python
G.addEdge(U,V)
G.addEdge(U,X)
G.addEdge(X,V)
G.addEdge(Y,X)
G.addEdge(V,Y)
G.addEdge(W,Y)
G.addEdge(W,Z)
G.addEdge(Z,Z)
```


```python
dfs(G)
```

    Before
    U
    0
    0
    Before
    V
    0
    0
    Before
    Y
    0
    0
    Before
    X
    0
    0
    After
    X
    4
    5
    After
    Y
    3
    6
    After
    V
    2
    7
    After
    U
    1
    8
    Before
    W
    0
    0
    Before
    Z
    0
    0
    After
    Z
    10
    11
    After
    W
    9
    12
    


```python
W.f
```




    0




```python
Z.f
```




    0




```python

```
