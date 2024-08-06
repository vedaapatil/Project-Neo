# Union Size of Chunks

### Problem Statement

Write a function to split a list into smaller lists of a specified size and then find the size of the union of the chunks.

### Tags

```List```  ```Chunking```  ```Union Size```  


### Explanation

 This combines splitting a list into chunks with finding the size of the union of those chunks.
### Solution
```
6
```
### Pseudocode

```text
function unionSizeOfChunks(lstToChunk, chunkSize):
    # Split the list into chunks of given size
    chunks = [lstToChunk[i:i + chunkSize] for i in range(0, len(lstToChunk), chunkSize)]
    
    # Find the union of all chunks combined
    union = set()
    for chunk in chunks:
        union.update(chunk)
    
    return len(union)

```

### Implementation

#### Python Implementation
```python
def union_size_of_chunks(lst_to_chunk, chunk_size):
    # Split the list into chunks of given size
    chunks = [lst_to_chunk[i:i + chunk_size] for i in range(0, len(lst_to_chunk), chunk_size)]
    
    # Find the union of all chunks combined
    union = set()
    for chunk in chunks:
        union.update(chunk)
    
    return len(union)

# Sample Input
lst_to_chunk = [1, 2, 3, 4, 5, 6, 7, 8]
chunk_size = 3
print(union_size_of_chunks(lst_to_chunk, chunk_size))  # Output: 6

```
#### Java Implementation
```java
import java.util.HashSet;
import java.util.List;
import java.util.Set;

public class UnionSizeOfChunks {
    public static int unionSizeOfChunks(List<Integer> lstToChunk, int chunkSize) {
        // Split the list into chunks of given size
        Set<Integer> union = new HashSet<>();
        for (int i = 0; i < lstToChunk.size(); i += chunkSize) {
            List<Integer> chunk = lstToChunk.subList(i, Math.min(i + chunkSize, lstToChunk.size()));
            union.addAll(chunk);
        }
        
        return union.size();
    }

    public static void main(String[] args) {
        List<Integer> lstToChunk = List.of(1, 2, 3, 4, 5, 6, 7, 8);
        int chunkSize = 3;
        System.out.println(unionSizeOfChunks(lstToChunk, chunkSize));  // Output: 6
    }
}

```
#### C++ Implementation
```cpp
#include <iostream>
#include <vector>
#include <set>
using namespace std;

int unionSizeOfChunks(const vector<int>& lstToChunk, int chunkSize) {
    // Split the list into chunks of given size
    set<int> unionSet;
    for (size_t i = 0; i < lstToChunk.size(); i += chunkSize) {
        vector<int> chunk(lstToChunk.begin() + i, lstToChunk.begin() + min(i + chunkSize, lstToChunk.size()));
        unionSet.insert(chunk.begin(), chunk.end());
    }
    
    return unionSet.size();
}

int main() {
    vector<int> lstToChunk = {1, 2, 3, 4, 5, 6, 7, 8};
    int chunkSize = 3;
    cout << unionSizeOfChunks(lstToChunk, chunkSize) << endl;  // Output: 6
    return 0;
}

```
***
***Problem Created and Solved by Ms. Veda Patil***
