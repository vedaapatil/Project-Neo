# Maximum Flow with Limited Capacity Augmentation

### Problem Statement

You are given a directed graph with `N` nodes and `M` edges, each edge having a certain capacity. You need to find the maximum flow from a source node `S` to a sink node `T`. However, the graph has a unique constraint: each augmenting path can increase the flow by at most a certain value `L`. Your task is to determine the maximum flow that can be achieved under this constraint.
The required values are:
```
N = 4
M = 5
Edges = [(1, 2, 10), (1, 3, 5), (2, 3, 15), (2, 4, 10), (3, 4, 10)]
S = 1
T = 4
L = 5
```

### Tags

```Graph Theory```  ```Max Flow```  ```Optimization``` 

### Explanation

To solve this problem, we use a modified version of the Ford-Fulkerson algorithm or the Edmonds-Karp algorithm, ensuring that each augmenting path found increases the flow by at most `L`.

### Solution
```
15
```
### Pseudocode

```text
FUNCTION max_flow_with_limited_augmentation(N, M, Edges, S, T, L):
    Initialize a graph with capacities as given by Edges
    Initialize max_flow to 0

    WHILE there exists an augmenting path from S to T:
        Find the minimum residual capacity along the path, `path_flow`
        IF path_flow > L:
            path_flow = L
        Update the capacities of the edges along the path
        Increment max_flow by path_flow

    RETURN max_flow
```

### Implementation

#### Python Implementation
```python
from collections import defaultdict, deque

def bfs_capacity_limited(graph, residual_graph, source, sink, parent, L):
    visited = set()
    queue = deque([source])
    visited.add(source)

    while queue:
        u = queue.popleft()

        for v, capacity in residual_graph[u].items():
            if v not in visited and capacity > 0:
                visited.add(v)
                parent[v] = u
                if v == sink:
                    return True
                queue.append(v)
    return False

def max_flow_with_limited_augmentation(N, M, Edges, S, T, L):
    graph = defaultdict(dict)
    residual_graph = defaultdict(dict)

    for u, v, capacity in Edges:
        graph[u][v] = capacity
        residual_graph[u][v] = capacity
        residual_graph[v][u] = 0

    max_flow = 0
    parent = {}

    while bfs_capacity_limited(graph, residual_graph, S, T, parent, L):
        path_flow = float('Inf')
        s = T

        while s != S:
            path_flow = min(path_flow, residual_graph[parent[s]][s])
            s = parent[s]

        path_flow = min(path_flow, L)
        v = T
        while v != S:
            u = parent[v]
            residual_graph[u][v] -= path_flow
            residual_graph[v][u] += path_flow
            v = parent[v]

        max_flow += path_flow

    return max_flow

# Example usage
N = 4
M = 5
Edges = [(1, 2, 10), (1, 3, 5), (2, 3, 15), (2, 4, 10), (3, 4, 10)]
S = 1
T = 4
L = 5
print(max_flow_with_limited_augmentation(N, M, Edges, S, T, L))  # Output should be 15
```
#### Java Implementation
```java
import java.util.*;

public class MaxFlowLimitedAugmentation {
    private static boolean bfs(int[][] residualGraph, int source, int sink, int[] parent, int L) {
        boolean[] visited = new boolean[residualGraph.length];
        Queue<Integer> queue = new LinkedList<>();
        queue.add(source);
        visited[source] = true;

        while (!queue.isEmpty()) {
            int u = queue.poll();

            for (int v = 0; v < residualGraph.length; v++) {
                if (!visited[v] && residualGraph[u][v] > 0) {
                    queue.add(v);
                    parent[v] = u;
                    visited[v] = true;
                    if (v == sink) {
                        return true;
                    }
                }
            }
        }
        return false;
    }

    public static int maxFlow(int[][] graph, int source, int sink, int L) {
        int u, v;
        int[][] residualGraph = new int[graph.length][graph[0].length];

        for (u = 0; u < graph.length; u++) {
            for (v = 0; v < graph[u].length; v++) {
                residualGraph[u][v] = graph[u][v];
            }
        }

        int[] parent = new int[graph.length];
        int maxFlow = 0;

        while (bfs(residualGraph, source, sink, parent, L)) {
            int pathFlow = Integer.MAX_VALUE;
            for (v = sink; v != source; v = parent[v]) {
                u = parent[v];
                pathFlow = Math.min(pathFlow, residualGraph[u][v]);
            }

            pathFlow = Math.min(pathFlow, L);

            for (v = sink; v != source; v = parent[v]) {
                u = parent[v];
                residualGraph[u][v] -= pathFlow;
                residualGraph[v][u] += pathFlow;
            }

            maxFlow += pathFlow;
        }
        return maxFlow;
    }

    public static void main(String[] args) {
        int N = 4;
        int M = 5;
        int[][] graph = {
            {0, 10, 5, 0},
            {0, 0, 15, 10},
            {0, 0, 0, 10},
            {0, 0, 0, 0}
        };
        int S = 0;
        int T = 3;
        int L = 5;
        System.out.println(maxFlow(graph, S, T, L));  // Output should be 15
    }
}
```
#### C++ Implementation
```cpp
#include <iostream>
#include <vector>
#include <queue>
#include <climits>
#include <cstring>

using namespace std;

bool bfs(vector<vector<int>>& residualGraph, int source, int sink, int parent[], int L) {
    int n = residualGraph.size();
    vector<bool> visited(n, false);
    queue<int> q;
    q.push(source);
    visited[source] = true;

    while (!q.empty()) {
        int u = q.front();
        q.pop();

        for (int v = 0; v < n; v++) {
            if (!visited[v] && residualGraph[u][v] > 0) {
                q.push(v);
                parent[v] = u;
                visited[v] = true;
                if (v == sink) {
                    return true;
                }
            }
        }
    }
    return false;
}

int maxFlow(vector<vector<int>>& graph, int source, int sink, int L) {
    int u, v;
    int n = graph.size();
    vector<vector<int>> residualGraph(n, vector<int>(n));

    for (u = 0; u < n; u++) {
        for (v = 0; v < n; v++) {
            residualGraph[u][v] = graph[u][v];
        }
    }

    int parent[n];
    int maxFlow = 0;

    while (bfs(residualGraph, source, sink, parent, L)) {
        int pathFlow = INT_MAX;
        for (v = sink; v != source; v = parent[v]) {
            u = parent[v];
            pathFlow = min(pathFlow, residualGraph[u][v]);
        }

        pathFlow = min(pathFlow, L);

        for (v = sink; v != source; v = parent[v]) {
            u = parent[v];
            residualGraph[u][v] -= pathFlow;
            residualGraph[v][u] += pathFlow;
        }

        maxFlow += pathFlow;
    }

    return maxFlow;
}

int main() {
    int N = 4;
    int M = 5;
    vector<vector<int>> graph = {
        {0, 10, 5, 0},
        {0, 0, 15, 10},
        {0, 0, 0, 10},
        {0, 0, 0, 0}
    };
    int S = 0;
    int T = 3;
    int L = 5;
    cout << maxFlow(graph, S, T, L) << endl;  // Output should be 15

    return 0;
}
```
***
***Problem Created and Solved by Ms. Veda Patil***
