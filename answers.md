# CMPS 2200 Assignment 4
## Answers

**Name:** Davis Voelkel






- **1a.** A d-ary heap has at most $d^i$ nodes on each level, so 1 node at level 0, d nodes at level 1, $ d^2 $ nodes at level 2, and so on. The maximum depth of this heap is $log_d n$.


- **1b.** For the insert function, the node is placed at the first free leaf, and it is compared to the parent at each level, at most $log_d n$ times. Therefore $W(n) \in O(log_d n)$. For delete min element, you take the right-most child of the root as the new root and you have to find the minimmum of d children $log_d n$ times, which is $ O(d* log_d n)$.


- **1c.** For Dijkstra's Algorithm, the heap is at most size |V|, so n= |V|. The number of delete-min calls is |V| since each node is removed from the heap once. Therefore the total work of delete-min is $O(|V|*log_d |V|)$. The number of insertions is at most |E| since each can cause at most 1 update. Therefore, the total work of insert is $O(|E|*log_d|V|)$. Therefore the total work of Dijkstra's Algorithm with d-ary heap is $O( |V|*log_d |V| + |E|*log_d|V|)$.

- **1d.** If you chose d = $|V|^\epsilon$, the log approach one as epsilon approaches, leaving you with $O( 1 + |E|) \in O(|E|) $.
- **2a.** For k=0, we can use 0 as an intermediate node, so (0,1,0) = -2 , (1,2,0) = 0, and (0,2,0)= 2. For k=1, we can use 0 or 1 as an intermediate node, (0,1,1) = -2, (1,2,1) = 0, and (0,2,1) = -1. For k=2, we can use 0,1,or 2 (0,1,2) = -2, (1,2,2) =0, and (0,2,2) = -1. 


- **2b.** It seems that for k=2, for each combination of i and j you take the minimum of the cost of the path using k=1 as intermediate for i and j and the paths where k=i,j with intermediate k =1. Therefore, APSP(i,j,2) = min(APSP(i,j,1), APSP(2,j,1) + APSP(i,2,1)).


- **2c.** The general optimal substructure is APSP(i,j,k) = min(APSP(i,j,k-1), APSP(k,j,k=1) + APSP(i,k,k-1)).

- **2d.** Since i,j,k are node sets from 1 to n. We have $n^3$ possible subproblems. Since i,j,k refer to nodes, n= |V|, so the work is $O(|V|^3)$

- **2e.** The work of Johnson's Algorithm is $O(|E||V|log|E|)$ ,which is less than $O(|V|^3)$ unless the graph is very dense. This is due to only Johnson's Algorithm relying on |E| here, so if |E| >= |V|^2, our algorithm is preferable.

- **3a.** A spanning tree has v-1 edges and no cycles and the minimal spanning tree is the spanning tree were the summation of the edge weights is the lowest. Say the max edge in an MST is e, then e is the minimum edge to cross the cut in the tree, by the Cut Property. An MMET however, purely aims to minimum the most expensive edge in the tree. Therefore, all MSTs are MMET's but not all MMEt's are MSTs, since the reduced overall sum includes the minimizing of the max edge, but not vice versa.


- **3b.**
To find the next best spanning tree after the MST, first compute the MST and call its weight W. Then, for every edge not in the MST, temporarily add it to the tree, creating exactly one cycle. On that cycle, remove the heaviest edge, which produces a new valid spanning tree with weight W' > W.

- **3c.** For |E| edges, you find the heaviest edge which takes O(|V|), therefore, the algorithm is $O(|E||V|)$.
