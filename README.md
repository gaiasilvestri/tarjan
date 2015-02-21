Tarjan
======
Find the strongly connected components of a directed graph (cyclic or acyclic)
------
A Matlab iterative version of Tarjan's algorithm to find the strongly connected components in a directed graph (cyclic or acyclic). Each component found is returned as the edges making it up. The input is a sparse matrix, where non-zero cells indicate a synaptic connection in the neural network represented. 
----
This program can deal with any graph represented by a matrix in Matlab! 

Use it if you need to:
- check if there are strongly connected components (sub-graphs where every node can be reached by every other node) in your graph
- check how large these components are
- check what edges and nodes make them up
