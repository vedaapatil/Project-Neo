# Sum of List Elements with Occurrence Count

### Problem Statement

Write a function to calculate the sum of all elements in a list and count the occurrences of a specific element.

### Tags

```List```  ```Sum```  ```Occurrences```  ```Count```   



### Explanation

This combines calculating the sum of list elements and counting the occurrences of a specific element.
### Solution
```
(19, 3)
```
### Pseudocode

```text

function sumAndCountOccurrences(list, element):
    total_sum = 0
    count = 0
    
    for item in list:
        total_sum += item
        if item == element:
            count += 1
    
    return (total_sum, count)

```

### Implementation

#### Python Implementation
```python
def sum_and_count_occurrences(lst, element):
    total_sum = 0
    count = 0
    
    for item in lst:
        total_sum += item
        if item == element:
            count += 1
    
    return (total_sum, count)

# Sample Input
lst = [4, 5, 6, 4, 4]
element = 4
print(sum_and_count_occurrences(lst, element))  # Output: (19, 3)

```
#### Java Implementation
```java
public class SumAndCountOccurrences {
    public static int[] sumAndCountOccurrences(int[] list, int element) {
        int totalSum = 0;
        int count = 0;
        
        for (int num : list) {
            totalSum += num;
            if (num == element) {
                count++;
            }
        }
        
        return new int[] { totalSum, count };
    }

    public static void main(String[] args) {
        int[] list = {4, 5, 6, 4, 4};
        int element = 4;
        int[] result = sumAndCountOccurrences(list, element);
        System.out.println(result[0] + ", " + result[1]);  // Output: 19, 3
    }
}


 
    

```
#### C++ Implementation
```cpp
#include <iostream>
#include <vector>
using namespace std;

pair<int, int> sumAndCountOccurrences(const vector<int>& lst, int element) {
    int totalSum = 0;
    int count = 0;
    
    for (int num : lst) {
        totalSum += num;
        if (num == element) {
            count++;
        }
    }
    
    return make_pair(totalSum, count);
}

int main() {
    vector<int> lst = {4, 5, 6, 4, 4};
    int element = 4;
    pair<int, int> result = sumAndCountOccurrences(lst, element);
    cout << result.first << ", " << result.second << endl;  // Output: 19, 3
    return 0;
}


```
***
***Problem Created and Solved by Ms. Veda Patil***
