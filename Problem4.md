
# Hypergraph Weight Minimization

### Problem Statement

You are given a weighted undirected hypergraph `H` consisting of `N` nodes and `M` hyperedges. A hyperedge is a generalized edge that can connect any number of nodes, and each hyperedge has an associated weight. Your task is to find the minimum possible sum of weights of a set of hyperedges such that every pair of nodes in the graph is connected either directly by a hyperedge or through a sequence of hyperedges.
Here are our values:
```
N = 5
M = 4
Hyperedges = [([1, 2, 3], 10),
    ([2, 3, 4], 15),
    ([1, 4, 5], 25),
    ([3, 5], 30)
]
```

### Tags

```Minimum Spanning Tree```  ```Hypergraphs``` ```Kruskal's & Prim's Algorithm``` 

### Explanation

This problem extends the concept of the minimum spanning tree (MST) to hypergraphs. In hypergraphs, each hyperedge can connect multiple nodes, making the problem more complex than in traditional graphs. The challenge is to determine a set of hyperedges with the minimum weight that ensures connectivity across all nodes.

### Solution

```
40
```

### Pseudocode

```text
FUNCTION find_min_hypergraph_weight(N, M, Hyperedges):
    Initialize a data structure to track connected components
    Sort hyperedges by weight
    total_weight = 0

    FOR each hyperedge in sorted hyperedges:
        IF hyperedge connects nodes from different components:
            Add hyperedge to the solution set
            Merge components
            total_weight += hyperedge's weight

    RETURN total_weight
```

### Solution

##### Python Implementation
``` python
class UnionFind:
    def __init__(self, n):
        self.parent = list(range(n))
        self.rank = [1] * n

    def find(self, node):
        if self.parent[node] != node:
            self.parent[node] = self.find(self.parent[node])
        return self.parent[node]

    def union(self, node1, node2):
        root1 = self.find(node1)
        root2 = self.find(node2)

        if root1 != root2:
            if self.rank[root1] > self.rank[root2]:
                self.parent[root2] = root1
            elif self.rank[root1] < self.rank[root2]:
                self.parent[root1] = root2
            else:
                self.parent[root2] = root1
                self.rank[root1] += 1

def find_min_hypergraph_weight(N, M, Hyperedges):
    uf = UnionFind(N)
    Hyperedges.sort(key=lambda x: x[1])  # Sort by weight

    total_weight = 0
    for edge in Hyperedges:
        nodes, weight = edge
        components = set(uf.find(node) for node in nodes)
        if len(components) > 1:  # If the hyperedge connects different components
            total_weight += weight
            for node in nodes:
                uf.union(nodes[0], node)

    return total_weight
```
##### Java Implementation
``` java
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

class Hyperedge {
    int[] nodes;
    int weight;

    Hyperedge(int[] nodes, int weight) {
        this.nodes = nodes;
        this.weight = weight;
    }
}

class UnionFind {
    private int[] parent;
    private int[] rank;

    UnionFind(int n) {
        parent = new int[n];
        rank = new int[n];
        for (int i = 0; i < n; i++) {
            parent[i] = i;
            rank[i] = 1;
        }
    }

    int find(int node) {
        if (parent[node] != node) {
            parent[node] = find(parent[node]);
        }
        return parent[node];
    }

    void union(int node1, int node2) {
        int root1 = find(node1);
        int root2 = find(node2);

        if (root1 != root2) {
            if (rank[root1] > rank[root2]) {
                parent[root2] = root1;
            } else if (rank[root1] < rank[root2]) {
                parent[root1] = root2;
            } else {
                parent[root2] = root1;
                rank[root1]++;
            }
        }
    }
}

public class HypergraphWeightMinimization {
    public static int findMinHypergraphWeight(int N, List<Hyperedge> hyperedges) {
        UnionFind uf = new UnionFind(N);
        Collections.sort(hyperedges, (a, b) -> a.weight - b.weight);

        int totalWeight = 0;
        for (Hyperedge edge : hyperedges) {
            int[] nodes = edge.nodes;
            int weight = edge.weight;

            int representative = uf.find(nodes[0]);
            boolean differentComponent = false;
            for (int node : nodes) {
                if (uf.find(node) != representative) {
                    differentComponent = true;
                    uf.union(representative, node);
                }
            }

            if (differentComponent) {
                totalWeight += weight;
            }
        }

        return totalWeight;
    }

    public static void main(String[] args) {
        List<Hyperedge> hyperedges = new ArrayList<>();
        hyperedges.add(new Hyperedge(new int[]{0, 1, 2}, 10));
        hyperedges.add(new Hyperedge(new int[]{1, 2, 3}, 15));
        hyperedges.add(new Hyperedge(new int[]{0, 3, 4}, 25));
        hyperedges.add(new Hyperedge(new int[]{2, 4}, 30));

        int result = findMinHypergraphWeight(5, hyperedges);
        System.out.println(result);
    }
}
```
##### C++ Implementation
``` cpp
#include <iostream>
#include <vector>
#include <algorithm>
#include <numeric>
#include <unordered_set>

using namespace std;

class UnionFind {
public:
    UnionFind(int n) : parent(n), rank(n, 1) {
        iota(parent.begin(), parent.end(), 0);
    }

    int find(int node) {
        if (parent[node] != node) {
            parent[node] = find(parent[node]);
        }
        return parent[node];
    }

    void unite(int node1, int node2) {
        int root1 = find(node1);
        int root2 = find(node2);

        if (root1 != root2) {
            if (rank[root1] > rank[root2]) {
                parent[root2] = root1;
            } else if (rank[root1] < rank[root2]) {
                parent[root1] = root2;
            } else {
                parent[root2] = root1;
                rank[root1]++;
            }
        }
    }

private:
    vector<int> parent;
    vector<int> rank;
};

struct Hyperedge {
    vector<int> nodes;
    int weight;

    bool operator<(const Hyperedge& other) const {
        return weight < other.weight;
    }
};

int findMinHypergraphWeight(int N, vector<Hyperedge>& hyperedges) {
    UnionFind uf(N);
    sort(hyperedges.begin(), hyperedges.end());

    int totalWeight = 0;
    for (const auto& edge : hyperedges) {
        unordered_set<int> components;
        for (int node : edge.nodes) {
            components.insert(uf.find(node));
        }
        if (components.size() > 1) {
            totalWeight += edge.weight;
            for (int node : edge.nodes) {
                uf.unite(edge.nodes[0], node);
            }
        }
    }

    return totalWeight;
}

int main() {
    vector<Hyperedge> hyperedges = {
        {{0, 1, 2}, 10},
        {{1, 2, 3}, 15},
        {{0, 3, 4}, 25},
        {{2, 4}, 30}
    };

    int result = findMinHypergraphWeight(5, hyperedges);
    cout << result << endl;

    return 0;
}
```
***
***Problem Created and Solved by Ms. Veda Patil***
