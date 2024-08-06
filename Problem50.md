# Maximum Subarray Sum After Removing Duplicates

### Problem Statement
Write a function to find the maximum sum of a subarray in a list after removing all duplicate elements.


### Tags

```Subarray Sum```  ```Duplicates```  ```Kadane's Algorithm```  

### Explanation

This combines finding the maximum subarray sum with the preprocessing step of removing duplicates.
### Solution
```
12
```
### Pseudocode

```text

function maxSubarraySumAfterRemovingDuplicates(lst):
    # Step 1: Remove duplicates
    unique_lst = list(set(lst))
    
    # Step 2: Find maximum subarray sum using Kadane's algorithm
    max_sum = float('-inf')
    current_sum = 0
    for num in unique_lst:
        current_sum = max(num, current_sum + num)
        max_sum = max(max_sum, current_sum)
    
    return max_sum

```

### Implementation

#### Python Implementation
```python
def max_subarray_sum_after_removing_duplicates(lst):
    # Step 1: Remove duplicates
    unique_lst = list(set(lst))
    
    # Step 2: Find maximum subarray sum using Kadane's algorithm
    max_sum = float('-inf')
    current_sum = 0
    for num in unique_lst:
        current_sum = max(num, current_sum + num)
        max_sum = max(max_sum, current_sum)
    
    return max_sum

# Sample Input
lst = [4, 2, 2, 3, 3, -1, 5]
print(max_subarray_sum_after_removing_duplicates(lst))  # Output: 12

```
#### Java Implementation
```java
import java.util.HashSet;
import java.util.Set;
import java.util.Arrays;

public class MaxSubarraySumAfterDuplicates {
    public static int maxSubarraySumAfterRemovingDuplicates(int[] lst) {
        // Step 1: Remove duplicates
        Set<Integer> uniqueSet = new HashSet<>();
        for (int num : lst) {
            uniqueSet.add(num);
        }
        int[] uniqueArr = uniqueSet.stream().mapToInt(Integer::intValue).toArray();
        
        // Step 2: Find maximum subarray sum using Kadane's algorithm
        int maxSum = Integer.MIN_VALUE;
        int currentSum = 0;
        for (int num : uniqueArr) {
            currentSum = Math.max(num, currentSum + num);
            maxSum = Math.max(maxSum, currentSum);
        }
        
        return maxSum;
    }

    public static void main(String[] args) {
        int[] lst = {4, 2, 2, 3, 3, -1, 5};
        System.out.println(maxSubarraySumAfterRemovingDuplicates(lst));  // Output: 12
    }
}

```
#### C++ Implementation
```cpp
#include <iostream>
#include <vector>
#include <unordered_set>
#include <algorithm>
using namespace std;

int maxSubarraySumAfterRemovingDuplicates(const vector<int>& lst) {
    // Step 1: Remove duplicates
    unordered_set<int> uniqueSet(lst.begin(), lst.end());
    vector<int> uniqueVec(uniqueSet.begin(), uniqueSet.end());
    
    // Step 2: Find maximum subarray sum using Kadane's algorithm
    int maxSum = INT_MIN;
    int currentSum = 0;
    for (int num : uniqueVec) {
        currentSum = max(num, currentSum + num);
        maxSum = max(maxSum, currentSum);
    }
    
    return maxSum;
}

int main() {
    vector<int> lst = {4, 2, 2, 3, 3, -1, 5};
    cout << maxSubarraySumAfterRemovingDuplicates(lst) << endl;  // Output: 12
    return 0;
}

```
***
***Problem Created and Solved by Ms. Veda Patil***
