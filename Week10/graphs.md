# Graphs

## Objective
Implement Breadth-first search and Depth-first search algorithms in C++

## Tasks
1. Create a theoretical graph using a pen and paper OR electronically. **(2 points)**

<img width="347" height="392" alt="image" src="https://github.com/user-attachments/assets/d86ea81e-acc9-4efd-828b-08d6dc507583" />

3. Implement the graph created in step 1 and apply breadth and depth-first search algorithms using C++. **(6 points)**


```cpp
#include <iostream>
#include <list>
#include <queue>
#include <stack>
#include <map>
using namespace std;

class Graph {
private:
    map<int, list<int>> adjList;  // adjacency list representation

public:
    // add a directed edge from u to v
    void addEdge(int u, int v) {
        adjList[u].push_back(v);
    }

    // Breadth First Search
    void BFS(int start) {
        map<int, bool> visited;
        queue<int> q;

        visited[start] = true;
        q.push(start);

        cout << "BFS starting from vertex " << start << ": ";

        while (!q.empty()) {
            int node = q.front();
            q.pop();
            cout << node << " ";

            for (int neighbor : adjList[node]) {
                if (!visited[neighbor]) {
                    visited[neighbor] = true;
                    q.push(neighbor);
                }
            }
        }
        cout << endl;
    }

    // Depth First Search helper
    void DFSUtil(int node, map<int, bool>& visited) {
        visited[node] = true;
        cout << node << " ";

        for (int neighbor : adjList[node]) {
            if (!visited[neighbor])
                DFSUtil(neighbor, visited);
        }
    }

    // Depth First Search
    void DFS(int start) {
        map<int, bool> visited;
        cout << "DFS starting from vertex " << start << ": ";
        DFSUtil(start, visited);
        cout << endl;
    }
};

int main() {
    Graph g;

    // Edges from the image
    g.addEdge(4, 2);
    g.addEdge(2, 6);
    g.addEdge(6, 7);
    g.addEdge(7, 5);
    g.addEdge(5, 4);
    g.addEdge(4, 3);
    g.addEdge(3, 7);

    // Run BFS and DFS
    g.BFS(4);  // starting from node 4
    g.DFS(4);  // starting from node 4

    return 0;
}
```

4. Compare both search algorithms in the context of Big O notations. **(2 points)**

The time complexity for both BFS and DFS is O(V+E) where V is the number of vertices and E is the number of edges.  This means they are both linear in terms of Big O complexity.
