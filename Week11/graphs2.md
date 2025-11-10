# Graphs

## Objective
Understanding Dijkstra's algorithm

## Tasks
1. Explain with the help of an example __"Why Dijkstra's algorithm fails on negative weights"__.

Dijkstra’s algorithm assumes that once a node’s shortest distance is found, it will never change. This assumption only holds true when all edge weights are non-negative. If a graph contains negative-weight edges, the algorithm may produce incorrect results because it might finalize a node’s distance too early—before discovering a shorter path through a negative edge.
