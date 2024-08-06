# Smallest Missing Positive Integer After Equal Subarray

### Problem Statement
Write a function to find the smallest missing positive integer from a list of unsorted integers, and then find the length of the longest subarray with an equal number of 0s and 1s in the same list.

### Tags

```Missing Integer```  ```Subarray```  ```Equal 0s and 1s``` 


### Explanation

 This combines finding the smallest missing positive integer with identifying the length of the longest subarray with an equal number of 0s and 1s.
### Solution
```
 2
```
### Pseudocode

```text

function smallestMissingPositiveAndLongestEqualSubarray(lst):
    # Find the smallest missing positive integer
    seen = set(lst)
    missing = 1
    while missing in seen:
        missing += 1
    
    # Find the longest subarray with equal number of 0s and 1s
    balance_map = {0: -1}
    balance = 0
    max_length = 0
    for i in range(len(lst)):
        balance += 1 if lst[i] == 1 else -1
        if balance in balance_map:
            max_length = max(max_length, i - balance_map[balance])
        else:
            balance_map[balance] = i
    
    return (missing, max_length)

```

### Implementation

#### Python Implementation
```python
def smallest_missing_positive_and_longest_equal_subarray(lst):
    # Find the smallest missing positive integer
    seen = set(lst)
    missing = 1
    while missing in seen:
        missing += 1
    
    # Find the longest subarray with equal number of 0s and 1s
    balance_map = {0: -1}
    balance = 0
    max_length = 0
    for i in range(len(lst)):
        balance += 1 if lst[i] == 1 else -1
        if balance in balance_map:
            max_length = max(max_length, i - balance_map[balance])
        else:
            balance_map[balance] = i
    
    return (missing, max_length)

# Sample Input
lst = [1, 0, 1, 3, 4, 0, 1, 2]
print(smallest_missing_positive_and_longest_equal_subarray(lst))  # Output: (2, 6)

```
#### Java Implementation
```java
import java.util.HashMap;
import java.util.HashSet;
import java.util.List;
import java.util.Map;
import java.util.Set;

public class MissingIntegerAndEqualSubarray {
    public static int[] smallestMissingPositiveAndLongestEqualSubarray(List<Integer> lst) {
        // Find the smallest missing positive integer
        Set<Integer> seen = new HashSet<>(lst);
        int missing = 1;
        while (seen.contains(missing)) {
            missing++;
        }
        
        // Find the longest subarray with equal number of 0s and 1s
        Map<Integer, Integer> balanceMap = new HashMap<>();
        balanceMap.put(0, -1);
        int balance = 0;
        int maxLength = 0;
        for (int i = 0; i < lst.size(); i++) {
            balance += (lst.get(i) == 1) ? 1 : -1;
            if (balanceMap.containsKey(balance)) {
                maxLength = Math.max(maxLength, i - balanceMap.get(balance));
            } else {
                balanceMap.put(balance, i);
            }
        }
        
        return new int[]{missing, maxLength};
    }

    public static void main(String[] args) {
        List<Integer> lst = List.of(1, 0, 1, 3, 4, 0, 1, 2);
        int[] result = smallestMissingPositiveAndLongestEqualSubarray(lst);
        System.out.println("Smallest Missing Positive: " + result[0]);
        System.out.println("Longest Equal Subarray Length: " + result[1]);
    }
}

```
#### C++ Implementation
```cpp
#include <iostream>
#include <vector>
#include <unordered_map>
#include <unordered_set>
using namespace std;

pair<int, int> smallestMissingPositiveAndLongestEqualSubarray(vector<int>& lst) {
    // Find the smallest missing positive integer
    unordered_set<int> seen(lst.begin(), lst.end());
    int missing = 1;
    while (seen.find(missing) != seen.end()) {
        missing++;
    }
    
    // Find the longest subarray with equal number of 0s and 1s
    unordered_map<int, int> balanceMap;
    balanceMap[0] = -1;
    int balance = 0;
    int maxLength = 0;
    for (size_t i = 0; i < lst.size(); i++) {
        balance += (lst[i] == 1) ? 1 : -1;
        if (balanceMap.find(balance) != balanceMap.end()) {
            maxLength = max(maxLength, (int)i - balanceMap[balance]);
        } else {
            balanceMap[balance] = i;
        }
    }
    
    return {missing, maxLength};
}

int main() {
    vector<int> lst = {1, 0, 1, 3, 4, 0, 1, 2};
    auto result = smallestMissingPositiveAndLongestEqualSubarray(lst);
    cout << "Smallest Missing Positive: " << result.first << endl;
    cout << "Longest Equal Subarray Length: " << result.second << endl;
    return 0;
}

```
***
***Problem Created and Solved by Ms. Veda Patil***
