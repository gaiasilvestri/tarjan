Tarjan
======
Find the strongly connected components of a directed graph represented by an adjacency matrix.
----
This program can deal with any graph represented by an adjacency matrix in Matlab! It has linear run time. 
  The MATLAB program takes an adjacency matrix as input, and outputs the strongly connected components found in the directed graph defined by the matrix. The algorithm closely follows Tarjan’s original version in terms of book keeping strategy and how the strongly connected components are found and removed from the stack. The critical difference is the way in which the successors of a node are selected during an exploration, since we avoid recursive calls.

  The program starts an exploration by visiting a node “n”, which is pushed to the stack and is assigned an index and a lowlink. The first node visited is node n=1, which corresponds to the 1st row of the input matrix. The program tries to find the first available edge leaving from node “n” by traversing the nth row of the adjacency matrix, looking for a non-zero cell. When a non-zero cell is found in the cth column, which stands for an available edge leaving node “n” to node “c”, we are taken to the successor node “c”. The successor node “c” and its outgoing edges are stored in the cth row of the same matrix. Iteratively, the program processes the cth row of the matrix if and only if node “c” was never visited. If it has been visited already, we only update its lowlink. If node “c” was never visited we go to its corresponding row in the matrix. We follow an edge to the next successor and repeat the aforementioned steps. We push unvisited nodes in the stack, and decline revisiting old ones. Backtracking ensures that every successor of the node where the exploration started is visited.

  When we finish visiting every successor of a node, we check whether a strongly connected component was found. This check is done in the same way as Tarjan’s original algorithm, by comparing the lowlink and index of the node “n” where the exploration started. If they are equal, we remove the strongly connected component from the stack.
As soon as we run out of edges leading from old nodes, we choose some unvisited node in the graph. If an unvisited node is available, we can begin a new exploration from this node. Eventually every edge in the graph will be traversed exactly once. If a node has no outgoing edges, some other unvisited node is selected to start a new exploration.

  The program keeps track of how many strongly connected components are found in total, and how many of those are made up of a single node. The program stores every strongly connected component it finds as a collection of edges, namely the ones connecting the nodes which belong to the component. Every edge is a pair of integers, which represent the origin and destination nodes linked by it. It follows that we can recover which nodes belong to a strongly connected component simply by inspecting each edge making up the component. Nodes whose in-degree or out-degree is 0, or belonging to an acyclic sub-graph, are returned as single-node components. These single- node components are stored as a single edge, which is a pair of integers figuring the relevant node and a zero.

