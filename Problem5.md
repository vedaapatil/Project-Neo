
# Path Weight Minimization in Weighted Tree

### Problem Statement

You are given a weighted, undirected tree with `N` nodes and `N-1` edges. Each edge has an associated weight. The tree is rooted at node 1. Your task is to find the minimum possible weight of a path from the root to any leaf such that the sum of the weights along the path is minimized.
The required values are:
```
N = 5
Edges = [
    (1, 2, 3),
    (1, 3, 5),
    (2, 4, 1),
    (2, 5, 2)
]
```

### Tags

```Data Structures```  ```Graph Theory``` ```Tree``` 

### Explanation

To solve this problem, we need to traverse the tree from the root to the leaves, keeping track of the path weights, and finding the minimum weight among all paths leading to a leaf node.

### Solution
```
4
```
### Pseudocode

```text
FUNCTION find_min_path_weight(N, Edges):
    Initialize a list to store the adjacency list for each node
    Populate the adjacency list with given edges
    FUNCTION dfs(node, current_weight):
        IF node is a leaf:
            UPDATE min_weight IF current_weight < min_weight
        FOR each child of node:
            CALL dfs(child, current_weight + weight of edge to child)
    CALL dfs(root, 0)
    RETURN min_weight
```

### Solution

#### Python Implementation
```python
def find_min_path_weight(N, Edges):
    from collections import defaultdict

    def dfs(node, weight):
        nonlocal min_weight
        is_leaf = True
        for child, edge_weight in graph[node]:
            is_leaf = False
            dfs(child, weight + edge_weight)
        if is_leaf:
            min_weight = min(min_weight, weight)

    graph = defaultdict(list)
    for u, v, w in Edges:
        graph[u].append((v, w))
        graph[v].append((u, w))

    min_weight = float('inf')
    dfs(1, 0)
    return min_weight

# Example usage
N = 5
Edges = [(1, 2, 3), (1, 3, 5), (2, 4, 1), (2, 5, 2)]
print(find_min_path_weight(N, Edges))
```
#### Java Implementation
```java
import java.util.*;

public class TreePathWeightMinimization {
    static class Edge {
        int to, weight;
        Edge(int to, int weight) {
            this.to = to;
            this.weight = weight;
        }
    }

    static int minWeight = Integer.MAX_VALUE;

    public static void main(String[] args) {
        int N = 5;
        List<Edge>[] graph = new ArrayList[N + 1];
        for (int i = 0; i <= N; i++) {
            graph[i] = new ArrayList<>();
        }

        graph[1].add(new Edge(2, 3));
        graph[1].add(new Edge(3, 5));
        graph[2].add(new Edge(1, 3));
        graph[2].add(new Edge(4, 1));
        graph[2].add(new Edge(5, 2));
        graph[3].add(new Edge(1, 5));
        graph[4].add(new Edge(2, 1));
        graph[5].add(new Edge(2, 2));

        boolean[] visited = new boolean[N + 1];
        dfs(graph, 1, 0, visited);

        System.out.println(minWeight);
    }

    public static void dfs(List<Edge>[] graph, int node, int weight, boolean[] visited) {
        visited[node] = true;
        boolean isLeaf = true;
        for (Edge edge : graph[node]) {
            if (!visited[edge.to]) {
                isLeaf = false;
                dfs(graph, edge.to, weight + edge.weight, visited);
            }
        }
        if (isLeaf) {
            minWeight = Math.min(minWeight, weight);
        }
        visited[node] = false;
    }
}
```
#### C++ Implementation
```cpp
#include <iostream>
#include <vector>
#include <algorithm>
#include <limits.h>

using namespace std;

struct Edge {
    int to, weight;
};

int minWeight = INT_MAX;

void dfs(vector<vector<Edge>>& graph, int node, int weight, vector<bool>& visited) {
    visited[node] = true;
    bool isLeaf = true;
    for (const auto& edge : graph[node]) {
        if (!visited[edge.to]) {
            isLeaf = false;
            dfs(graph, edge.to, weight + edge.weight, visited);
        }
    }
    if (isLeaf) {
        minWeight = min(minWeight, weight);
    }
    visited[node] = false;
}

int main() {
    int N = 5;
    vector<vector<Edge>> graph(N + 1);

    graph[1].push_back({2, 3});
    graph[1].push_back({3, 5});
    graph[2].push_back({1, 3});
    graph[2].push_back({4, 1});
    graph[2].push_back({5, 2});
    graph[3].push_back({1, 5});
    graph[4].push_back({2, 1});
    graph[5].push_back({2, 2});

    vector<bool> visited(N + 1, false);
    dfs(graph, 1, 0, visited);

    cout << minWeight << endl;

    return 0;
}
```
***
***Problem Created and Solved by Ms. Veda Patil***
