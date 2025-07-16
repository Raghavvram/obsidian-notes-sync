#### Prim's Algorithm for Minimum Spanning Tree

```java
MST-PRIM(G, w, r)
	for each u ∈ G.V
       u.key = ∞
       u.π = NIL
    r.key = 0
    Q = G.V
    while Q ≠ ∅
	    u = EXTRACT-MIN(Q)
	    for each v ∈ G.Adj[u]
		    if v ∈ Q and w(u, v) < v.key
			    v.π = u
			    v.key = w(u, v)
```

#### Kruskal's Algorithm for Minimum Spanning Tree

```java
MST-KRUSKAL(V,E)
	A = ∅
	for each v ∈ V
		make-disjoint-set(v)
	SORT E BY WEIGHT IN INCREASING ORDER
	for each (v1,v2) ∈ E
		if FIND(v1) != FIND(v2)
		A = A U {(v1,v2)}
		UNION(v1,v2)
	return A
```

#### Dijkstra's Algorithm Single Source Shortest Path

```java
DIJKSTRA(G,w,s)
	INITILIZE-SINGLE-SOURCE(G,s)
	s = ∅
	Q = G.v
	while Q != ∅
		u = EXTRACT-MIN(Q)
		s = s U {u}
		for each v ∈ G.adj[u]
			relax(u,v,w)
```