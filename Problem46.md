# Check Sorted After Removing Leading Zeros

### Problem Statement
Write a function to remove leading zeros from a list of integers and then check if the resulting list is sorted in non-decreasing order.

### Tags

```List```  ```Sorting```  ```Leading Zeros```  

### Explanation

This combines removing leading zeros with checking if the modified list is sorted.
### Solution
```
1 
```
### Pseudocode

```text
function isSortedAfterRemovingZeros(lst):
    # Remove leading zeros
    index = 0
    while index < len(lst) and lst[index] == 0:
        index += 1
    lst = lst[index:]
    
    # Check if the list is sorted in non-decreasing order
    for i in range(1, len(lst)):
        if lst[i] < lst[i - 1]:
            return 0  # Not sorted
    
    return 1  # Sorted

```

### Implementation

#### Python Implementation
```python

def is_sorted_after_removing_zeros(lst):
    # Remove leading zeros
    index = 0
    while index < len(lst) and lst[index] == 0:
        index += 1
    lst = lst[index:]
    
    # Check if the list is sorted in non-decreasing order
    for i in range(1, len(lst)):
        if lst[i] < lst[i - 1]:
            return 0  # Not sorted
    
    return 1  # Sorted

# Sample Input
lst = [0, 0, 3, 1, 4, 5, 0]
print(is_sorted_after_removing_zeros(lst))  # Output: 1

```
#### Java Implementation
```java
import java.util.List;

public class SortedAfterRemovingZeros {
    public static int isSortedAfterRemovingZeros(List<Integer> lst) {
        // Remove leading zeros
        int index = 0;
        while (index < lst.size() && lst.get(index) == 0) {
            index++;
        }
        lst = lst.subList(index, lst.size());
        
        // Check if the list is sorted in non-decreasing order
        for (int i = 1; i < lst.size(); i++) {
            if (lst.get(i) < lst.get(i - 1)) {
                return 0;  // Not sorted
            }
        }
        
        return 1;  // Sorted
    }

    public static void main(String[] args) {
        List<Integer> lst = List.of(0, 0, 3, 1, 4, 5, 0);
        System.out.println(isSortedAfterRemovingZeros(lst));  // Output: 1
    }
}


```
#### C++ Implementation
```cpp
#include <iostream>
#include <vector>
using namespace std;

int isSortedAfterRemovingZeros(vector<int>& lst) {
    // Remove leading zeros
    int index = 0;
    while (index < lst.size() && lst[index] == 0) {
        index++;
    }
    lst.erase(lst.begin(), lst.begin() + index);
    
    // Check if the list is sorted in non-decreasing order
    for (size_t i = 1; i < lst.size(); i++) {
        if (lst[i] < lst[i - 1]) {
            return 0;  // Not sorted
        }
    }
    
    return 1;  // Sorted
}

int main() {
    vector<int> lst = {0, 0, 3, 1, 4, 5, 0};
    cout << isSortedAfterRemovingZeros(lst) << endl;  // Output: 1
    return 0;
}

```
***
***Problem Created and Solved by Ms. Veda Patil***
