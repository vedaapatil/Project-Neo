# Largest Contiguous Subarray with Missing Positive Integer
### Problem Statement

Write a function to find the largest subarray with contiguous elements and then find the first missing positive integer from that subarray.

### Tags

```Subarray```  ``` Contiguous```  ```Missing Integer```  

### Explanation
This combines finding the largest contiguous subarray with identifying the first missing positive integer from that subarray.
### Solution
```
4
```
### Pseudocode

```text

function findLargestContiguousAndMissingPositive(lst):
    # Find the largest contiguous subarray
    largest_subarray = []
    current_subarray = [lst[0]]
    for i in range(1, len(lst)):
        if lst[i] == lst[i - 1] + 1:
            current_subarray.append(lst[i])
        else:
            if len(current_subarray) > len(largest_subarray):
                largest_subarray = current_subarray
            current_subarray = [lst[i]]
    
    if len(current_subarray) > len(largest_subarray):
        largest_subarray = current_subarray
    
    # Find the first missing positive integer in the largest subarray
    seen = set(largest_subarray)
    missing = 1
    while missing in seen:
        missing += 1
    
    return missing

```

### Implementation

#### Python Implementation
```python
def find_largest_contiguous_and_missing_positive(lst):
    # Find the largest contiguous subarray
    largest_subarray = []
    current_subarray = [lst[0]]
    for i in range(1, len(lst)):
        if lst[i] == lst[i - 1] + 1:
            current_subarray.append(lst[i])
        else:
            if len(current_subarray) > len(largest_subarray):
                largest_subarray = current_subarray
            current_subarray = [lst[i]]
    
    if len(current_subarray) > len(largest_subarray):
        largest_subarray = current_subarray
    
    # Find the first missing positive integer in the largest subarray
    seen = set(largest_subarray)
    missing = 1
    while missing in seen:
        missing += 1
    
    return missing

# Sample Input
lst = [1, 2, 3, 5, 6, 8, 9, 10]
print(find_largest_contiguous_and_missing_positive(lst))  # Output: 4

```
#### Java Implementation
```java
import java.util.HashSet;
import java.util.List;
import java.util.Set;

public class LargestContiguousAndMissingPositive {
    public static int findLargestContiguousAndMissingPositive(List<Integer> lst) {
        // Find the largest contiguous subarray
        List<Integer> largestSubarray = List.of();
        List<Integer> currentSubarray = List.of(lst.get(0));
        for (int i = 1; i < lst.size(); i++) {
            if (lst.get(i) == lst.get(i - 1) + 1) {
                currentSubarray.add(lst.get(i));
            } else {
                if (currentSubarray.size() > largestSubarray.size()) {
                    largestSubarray = currentSubarray;
                }
                currentSubarray = List.of(lst.get(i));
            }
        }
        if (currentSubarray.size() > largestSubarray.size()) {
            largestSubarray = currentSubarray;
        }
        
        // Find the first missing positive integer in the largest subarray
        Set<Integer> seen = new HashSet<>(largestSubarray);
        int missing = 1;
        while (seen.contains(missing)) {
            missing++;
        }
        
        return missing;
    }

    public static void main(String[] args) {
        List<Integer> lst = List.of(1, 2, 3, 5, 6, 8, 9, 10);
        System.out.println(findLargestContiguousAndMissingPositive(lst));  // Output: 4
    }
}


```
#### C++ Implementation
```cpp
#include <iostream>
#include <vector>
#include <set>
using namespace std;

int findLargestContiguousAndMissingPositive(vector<int>& lst) {
    // Find the largest contiguous subarray
    vector<int> largestSubarray;
    vector<int> currentSubarray = {lst[0]};
    for (size_t i = 1; i < lst.size(); i++) {
        if (lst[i] == lst[i - 1] + 1) {
            currentSubarray.push_back(lst[i]);
        } else {
            if (currentSubarray.size() > largestSubarray.size()) {
                largestSubarray = currentSubarray;
            }
            currentSubarray = {lst[i]};
        }
    }
    if (currentSubarray.size() > largestSubarray.size()) {
        largestSubarray = currentSubarray;
    }
    
    // Find the first missing positive integer in the largest subarray
    set<int> seen(largestSubarray.begin(), largestSubarray.end());
    int missing = 1;
    while (seen.find(missing) != seen.end()) {
        missing++;
    }
    
    return missing;
}

int main() {
    vector<int> lst = {1, 2, 3, 5, 6, 8, 9, 10};
    cout << findLargestContiguousAndMissingPositive(lst) << endl;  // Output: 4
    return 0;
}

```
***
***Problem Created and Solved by Ms. Veda Patil***
