# Product of List Elements with First Non-Repeating Element

### Problem Statement
Write a function to calculate the product of all elements in a list and find the first non-repeating element.


### Tags

```List```  ```Product```  ```Non-Repeating Element```  


### Explanation
This combines calculating the product of list elements with finding the first non-repeating element in the list.

### Solution
```
(240, 3) 
```
### Pseudocode

```text
function productAndFirstNonRepeating(lst):
    # Calculate the product of all elements
    product = 1
    for num in lst:
        product *= num
    
    # Find the first non-repeating element
    counts = {}
    for num in lst:
        if num in counts:
            counts[num] += 1
        else:
            counts[num] = 1
    
    for num in lst:
        if counts[num] == 1:
            first_non_repeating = num
            break
    
    return (product, first_non_repeating)

```

### Implementation

#### Python Implementation
```python
def product_and_first_non_repeating(lst):
    # Calculate the product of all elements
    product = 1
    for num in lst:
        product *= num
    
    # Find the first non-repeating element
    counts = {}
    for num in lst:
        if num in counts:
            counts[num] += 1
        else:
            counts[num] = 1
    
    first_non_repeating = None
    for num in lst:
        if counts[num] == 1:
            first_non_repeating = num
            break
    
    return (product, first_non_repeating)

# Sample Input
lst = [4, 2, 3, 4, 5, 2]
print(product_and_first_non_repeating(lst))  # Output: (240, 3)


```
#### Java Implementation
```java
import java.util.HashMap;
import java.util.Map;

public class ProductAndFirstNonRepeating {
    public static Object[] productAndFirstNonRepeating(int[] lst) {
        // Calculate the product of all elements
        int product = 1;
        for (int num : lst) {
            product *= num;
        }
        
        // Find the first non-repeating element
        Map<Integer, Integer> counts = new HashMap<>();
        for (int num : lst) {
            counts.put(num, counts.getOrDefault(num, 0) + 1);
        }
        
        int firstNonRepeating = -1;
        for (int num : lst) {
            if (counts.get(num) == 1) {
                firstNonRepeating = num;
                break;
            }
        }
        
        return new Object[] { product, firstNonRepeating };
    }

    public static void main(String[] args) {
        int[] lst = {4, 2, 3, 4, 5, 2};
        Object[] result = productAndFirstNonRepeating(lst);
        System.out.println(result[0] + ", " + result[1]);  // Output: 240, 3
    }
}


    

```
#### C++ Implementation
```cpp
#include <iostream>
#include <vector>
#include <unordered_map>
using namespace std;

pair<int, int> productAndFirstNonRepeating(const vector<int>& lst) {
    // Calculate the product of all elements
    int product = 1;
    for (int num : lst) {
        product *= num;
    }
    
    // Find the first non-repeating element
    unordered_map<int, int> counts;
    for (int num : lst) {
        counts[num]++;
    }
    
    int firstNonRepeating = -1;
    for (int num : lst) {
        if (counts[num] == 1) {
            firstNonRepeating = num;
            break;
        }
    }
    
    return make_pair(product, firstNonRepeating);
}

int main() {
    vector<int> lst = {4, 2, 3, 4, 5, 2};
    auto [product, firstNonRepeating] = productAndFirstNonRepeating(lst);
    cout << product << ", " << firstNonRepeating << endl;  // Output: 240, 3
    return 0;
}


```
***
***Problem Created and Solved by Ms. Veda Patil***
