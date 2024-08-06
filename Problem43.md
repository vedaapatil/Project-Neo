# Kth Smallest Element with Removal

### Problem Statement

Write a function to find the Kth smallest element in a list and remove all occurrences of a specific element from the list.

### Tags

```List```  ``` Kth Smallest```  ```Remove Element```  

### Explanation
This combines finding the Kth smallest element with removing all occurrences of a specified element from the list.

### Solution
```
 (3, [4, 2, 1, 5])
```
### Pseudocode

```text
function kthSmallestAndRemove(lst, k, elementToRemove):
    lst.sort()  # Sort the list
    kth_smallest = lst[k - 1]  # Find the Kth smallest element
    lst = [x for x in lst if x != elementToRemove]  # Remove all occurrences of the specified element
    return (kth_smallest, lst)

```

### Implementation

#### Python Implementation
```python
def kth_smallest_and_remove(lst, k, element_to_remove):
    lst.sort()  # Sort the list
    kth_smallest = lst[k - 1]  # Find the Kth smallest element
    lst = [x for x in lst if x != element_to_remove]  # Remove all occurrences of the specified element
    return (kth_smallest, lst)

# Sample Input
lst = [4, 2, 7, 1, 3, 7, 5]
k = 3
element_to_remove = 7
print(kth_smallest_and_remove(lst, k, element_to_remove))  # Output: (3, [4, 2, 1, 5])

```
#### Java Implementation
```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

public class KthSmallestAndRemoval {
    public static Object[] kthSmallestAndRemove(int[] lst, int k, int elementToRemove) {
        Arrays.sort(lst);  // Sort the list
        int kthSmallest = lst[k - 1];  // Find the Kth smallest element
        
        List<Integer> result = new ArrayList<>();
        for (int num : lst) {
            if (num != elementToRemove) {
                result.add(num);  // Remove all occurrences of the specified element
            }
        }
        
        return new Object[] { kthSmallest, result };
    }

    public static void main(String[] args) {
        int[] lst = {4, 2, 7, 1, 3, 7, 5};
        int k = 3;
        int elementToRemove = 7;
        Object[] result = kthSmallestAndRemove(lst, k, elementToRemove);
        System.out.println(result[0] + ", " + result[1]);  // Output: 3, [4, 2, 1, 5]
    }
}

 
    

```
#### C++ Implementation
```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

pair<int, vector<int>> kthSmallestAndRemove(vector<int> lst, int k, int elementToRemove) {
    sort(lst.begin(), lst.end());  // Sort the list
    int kthSmallest = lst[k - 1];  // Find the Kth smallest element
    
    lst.erase(remove(lst.begin(), lst.end(), elementToRemove), lst.end());  // Remove all occurrences of the specified element
    
    return make_pair(kthSmallest, lst);
}

int main() {
    vector<int> lst = {4, 2, 7, 1, 3, 7, 5};
    int k = 3;
    int elementToRemove = 7;
    auto [kthSmallest, result] = kthSmallestAndRemove(lst, k, elementToRemove);
    cout << kthSmallest << ", ";
    for (int num : result) {
        cout << num << " ";
    }
    cout << endl;  // Output: 3, 1 2 4 5
    return 0;
}


```
***
***Problem Created and Solved by Ms. Veda Patil***
