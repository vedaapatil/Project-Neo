# Third Largest Element with Positive and Negative Counts
### Problem Statement

Write a function to find the third largest element in a list and count the number of positive and negative numbers in the list.

### Tags

```List```  ```Third Largest```  ```Positive Count```  ```Negative Count```  

### Explanation

This combines finding the third largest element with counting positive and negative numbers in a list.
### Solution
```
 (5, 3, 2)
```
### Pseudocode

```text

function thirdLargestAndCounts(lst):
    largest = second_largest = third_largest = -infinity
    positive_count = 0
    negative_count = 0
    
    for num in lst:
        if num > largest:
            third_largest = second_largest
            second_largest = largest
            largest = num
        elif num > second_largest and num < largest:
            third_largest = second_largest
            second_largest = num
        elif num > third_largest and num < second_largest:
            third_largest = num
        
        if num > 0:
            positive_count += 1
        elif num < 0:
            negative_count += 1
    
    return (third_largest, positive_count, negative_count)


```

### Implementation

#### Python Implementation
```python
def third_largest_and_counts(lst):
    largest = second_largest = third_largest = float('-inf')
    positive_count = 0
    negative_count = 0
    
    for num in lst:
        if num > largest:
            third_largest = second_largest
            second_largest = largest
            largest = num
        elif num > second_largest and num < largest:
            third_largest = second_largest
            second_largest = num
        elif num > third_largest and num < second_largest:
            third_largest = num
        
        if num > 0:
            positive_count += 1
        elif num < 0:
            negative_count += 1
    
    return (third_largest, positive_count, negative_count)

# Sample Input
lst = [4, -1, 3, 7, -2, 5]
print(third_largest_and_counts(lst))  # Output: (5, 3, 2)

```
#### Java Implementation
```java
import java.util.ArrayList;
import java.util.List;

public class ThirdLargestAndCounts {
    public static int[] thirdLargestAndCounts(int[] lst) {
        int largest = Integer.MIN_VALUE;
        int secondLargest = Integer.MIN_VALUE;
        int thirdLargest = Integer.MIN_VALUE;
        int positiveCount = 0;
        int negativeCount = 0;
        
        for (int num : lst) {
            if (num > largest) {
                thirdLargest = secondLargest;
                secondLargest = largest;
                largest = num;
            } else if (num > secondLargest && num < largest) {
                thirdLargest = secondLargest;
                secondLargest = num;
            } else if (num > thirdLargest && num < secondLargest) {
                thirdLargest = num;
            }
            
            if (num > 0) positiveCount++;
            else if (num < 0) negativeCount++;
        }
        
        return new int[] { thirdLargest, positiveCount, negativeCount };
    }

    public static void main(String[] args) {
        int[] lst = {4, -1, 3, 7, -2, 5};
        int[] result = thirdLargestAndCounts(lst);
        System.out.println(result[0] + ", " + result[1] + ", " + result[2]);  // Output: 5, 3, 2
    }
}


```
#### C++ Implementation
```cpp
#include <iostream>
#include <vector>
#include <limits>
using namespace std;

tuple<int, int, int> thirdLargestAndCounts(const vector<int>& lst) {
    int largest = numeric_limits<int>::min();
    int secondLargest = numeric_limits<int>::min();
    int thirdLargest = numeric_limits<int>::min();
    int positiveCount = 0;
    int negativeCount = 0;
    
    for (int num : lst) {
        if (num > largest) {
            thirdLargest = secondLargest;
            secondLargest = largest;
            largest = num;
        } else if (num > secondLargest && num < largest) {
            thirdLargest = secondLargest;
            secondLargest = num;
        } else if (num > thirdLargest && num < secondLargest) {
            thirdLargest = num;
        }
        
        if (num > 0) positiveCount++;
        else if (num < 0) negativeCount++;
    }
    
    return make_tuple(thirdLargest, positiveCount, negativeCount);
}

int main() {
    vector<int> lst = {4, -1, 3, 7, -2, 5};
    auto [thirdLargest, positiveCount, negativeCount] = thirdLargestAndCounts(lst);
    cout << thirdLargest << ", " << positiveCount << ", " << negativeCount << endl;  // Output: 5, 3, 2
    return 0;
}

```
***
***Problem Created and Solved by Ms. Veda Patil***
