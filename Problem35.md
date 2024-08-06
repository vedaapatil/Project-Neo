# Second Max in List

### Problem Statement

Find the second largest element in a list.

### Tags

```Iteration```  ```Comparison```  ```List``` 




### Explanation
1. **Find maximum:**
    - Iterate to find the largest element.
2. **Find second maximum:** 
    - Iterate again to find the largest element smaller than the maximum.
### Solution
```
8
```
### Pseudocode

```text
1. Find max_element in list.
2. Initialize second_max to smallest value.
3. Loop through list:
   a. If element is not max_element and is greater than second_max:
      i. Update second_max.
4. Return second_max.

```

### Implementation

#### Python Implementation
```python
def second_max(lst):
    max_element = max(lst)
    second_max = float('-inf')
    for num in lst:
        if num != max_element and num > second_max:
            second_max = num
    return second_max

print(second_max([3, 8, 1, 10, 5]))  # Output: 8

```
#### Java Implementation
```java
public class Main {
    public static int secondMax(int[] lst) {
        int maxElement = Integer.MIN_VALUE;
        for (int num : lst) {
            if (num > maxElement) {
                maxElement = num;
            }
        }
        int secondMax = Integer.MIN_VALUE;
        for (int num : lst) {
            if (num != maxElement && num > secondMax) {
                secondMax = num;
            }
        }
        return secondMax;
    }

    public static void main(String[] args) {
        int[] lst = {3, 8, 1, 10, 5};
        System.out.println(secondMax(lst));  // Output: 8
    }
}

```
#### C++ Implementation
```cpp

  #include <iostream>
#include <vector>
#include <climits>

int secondMax(const std::vector<int>& lst) {
    int maxElement = INT_MIN;
    for (int num : lst) {
        if (num > maxElement) {
            maxElement = num;
        }
    }
    int secondMax = INT_MIN;
    for (int num : lst) {
        if (num != maxElement && num > secondMax) {
            secondMax = num;
        }
    }
    return secondMax;
}

int main() {
    std::vector<int> lst = {3, 8, 1, 10, 5};
    std::cout << secondMax(lst) << std::endl;  // Output: 8
    return 0;
}

```
***
***Problem Created and Solved by Ms. Veda Patil***
