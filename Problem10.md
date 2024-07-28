# Maximum XOR Subarray

### Problem Statement

You are given an array of integers `arr` of size `N`. Your task is to find the maximum XOR value that can be obtained by XORing all the elements of any contiguous subarray of `arr`.
The required value is:
```
arr = [8, 1, 2, 12, 7, 6]
```

### Tags

```Bit Manipulation```  ```Prefix XOR```  ```Data Structures``` 

### Explanation

To solve this problem, we use a data structure called a trie to store the prefix XORs. The trie helps in efficiently finding the maximum XOR of the current prefix XOR with previously stored prefix XORs. This approach leverages the properties of XOR to maximize the result.

### Solution
```
15
```
### Pseudocode

```text
FUNCTION find_maximum_xor_subarray(arr):
    Initialize a variable max_xor to 0
    Initialize a variable current_xor to 0
    Initialize a trie structure to store prefix XORs

    FOR each element in arr:
        current_xor = current_xor XOR element
        Insert current_xor into the trie
        Query the trie for the maximum XOR with current_xor
        Update max_xor if the queried value is greater

    RETURN max_xor
```

### Implementation

#### Python Implementation
```python
class TrieNode:
    def __init__(self):
        self.children = {}
        self.value = 0

class Trie:
    def __init__(self):
        self.root = TrieNode()
    
    def insert(self, num):
        node = self.root
        for i in range(31, -1, -1):
            bit = (num >> i) & 1
            if bit not in node.children:
                node.children[bit] = TrieNode()
            node = node.children[bit]
        node.value = num
    
    def query(self, num):
        node = self.root
        for i in range(31, -1, -1):
            bit = (num >> i) & 1
            toggled_bit = 1 - bit
            if toggled_bit in node.children:
                node = node.children[toggled_bit]
            else:
                node = node.children.get(bit, node)
        return num ^ node.value

def find_maximum_xor_subarray(arr):
    trie = Trie()
    max_xor = 0
    current_xor = 0

    trie.insert(0)  # To handle the case when subarray starts from index 0

    for num in arr:
        current_xor ^= num
        trie.insert(current_xor)
        max_xor = max(max_xor, trie.query(current_xor))

    return max_xor

# Example usage
arr = [8, 1, 2, 12, 7, 6]
print(find_maximum_xor_subarray(arr))  # Output should be 15
```
#### Java Implementation
```java
class TrieNode {
    TrieNode[] children = new TrieNode[2];
    int value;
}

class Trie {
    private TrieNode root = new TrieNode();

    public void insert(int num) {
        TrieNode node = root;
        for (int i = 31; i >= 0; i--) {
            int bit = (num >> i) & 1;
            if (node.children[bit] == null) {
                node.children[bit] = new TrieNode();
            }
            node = node.children[bit];
        }
        node.value = num;
    }

    public int query(int num) {
        TrieNode node = root;
        for (int i = 31; i >= 0; i--) {
            int bit = (num >> i) & 1;
            int toggledBit = 1 - bit;
            if (node.children[toggledBit] != null) {
                node = node.children[toggledBit];
            } else {
                node = node.children[bit];
            }
        }
        return num ^ node.value;
    }
}

public class MaxXORSubarray {
    public static int findMaximumXORSubarray(int[] arr) {
        Trie trie = new Trie();
        int maxXOR = 0;
        int currentXOR = 0;

        trie.insert(0);  // To handle the case when subarray starts from index 0

        for (int num : arr) {
            currentXOR ^= num;
            trie.insert(currentXOR);
            maxXOR = Math.max(maxXOR, trie.query(currentXOR));
        }

        return maxXOR;
    }

    public static void main(String[] args) {
        int[] arr = {8, 1, 2, 12, 7, 6};
        System.out.println(findMaximumXORSubarray(arr));  // Output should be 15
    }
}
```
#### C++ Implementation
```cpp
#include <iostream>
#include <vector>
#include <unordered_map>
using namespace std;

struct TrieNode {
    unordered_map<int, TrieNode*> children;
    int value;
    TrieNode() : value(0) {}
};

class Trie {
public:
    Trie() {
        root = new TrieNode();
    }
    
    void insert(int num) {
        TrieNode* node = root;
        for (int i = 31; i >= 0; i--) {
            int bit = (num >> i) & 1;
            if (node->children.find(bit) == node->children.end()) {
                node->children[bit] = new TrieNode();
            }
            node = node->children[bit];
        }
        node->value = num;
    }
    
    int query(int num) {
        TrieNode* node = root;
        for (int i = 31; i >= 0; i--) {
            int bit = (num >> i) & 1;
            int toggledBit = 1 - bit;
            if (node->children.find(toggledBit) != node->children.end()) {
                node = node->children[toggledBit];
            } else {
                node = node->children[bit];
            }
        }
        return num ^ node->value;
    }
    
private:
    TrieNode* root;
};

int findMaximumXORSubarray(vector<int>& arr) {
    Trie trie;
    int maxXOR = 0;
    int currentXOR = 0;

    trie.insert(0);  // To handle the case when subarray starts from index 0

    for (int num : arr) {
        currentXOR ^= num;
        trie.insert(currentXOR);
        maxXOR = max(maxXOR, trie.query(currentXOR));
    }

    return maxXOR;
}

int main() {
    vector<int> arr = {8, 1, 2, 12, 7, 6};
    cout << findMaximumXORSubarray(arr) << endl;  // Output should be 15
    return 0;
}
```
***
***Problem Created and Solved by Ms. Veda Patil***
