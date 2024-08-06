# Sum of Extremes

### Problem Statement

Find the sum of the maximum, minimum, and second largest elements in an array.


### Tags

``` Array```  ```Maximum```  ```Minimum```  ```Second Largest```   ```Sum``` 
 
### Explanation

Return the sum of the largest, smallest, and second largest numbers in the array.
### Solution
```
19
```
### Pseudocode

```text
function sumMaxMinSecondLargest(arr):
    if length of arr < 2:
        return "Invalid Input"

    max = min = second_max = arr[0]

    for element in arr:
        if element > max:
            second_max = max
            max = element
        elif element > second_max and element != max:
            second_max = element
        if element < min:
            min = element

    return max + min + second_max

```

### Implementation

#### Python Implementation
```python

def sum_max_min_second_largest(arr):
    if len(arr) < 2:
        return "Invalid Input"
    
    max_val = min_val = second_max_val = arr[0]
    
    for num in arr:
        if num > max_val:
            second_max_val = max_val
            max_val = num
        elif num > second_max_val and num != max_val:
            second_max_val = num
        if num < min_val:
            min_val = num

    return max_val + min_val + second_max_val

# Sample Input
arr = [5, 3, 9, 2, 8]
print(sum_max_min_second_largest(arr))  # Output: 19

```
#### Java Implementation
```java
public class SumMaxMinSecondLargest {
    public static int sumMaxMinSecondLargest(int[] arr) {
        if (arr.length < 2) {
            throw new IllegalArgumentException("Invalid Input");
        }

        int max = arr[0], min = arr[0], secondMax = arr[0];

        for (int num : arr) {
            if (num > max) {
                secondMax = max;
                max = num;
            } else if (num > secondMax && num != max) {
                secondMax = num;
            }
            if (num < min) {
                min = num;
            }
        }

        return max + min + secondMax;
    }

    public static void main(String[] args) {
        int[] arr = {5, 3, 9, 2, 8};
        System.out.println(sumMaxMinSecondLargest(arr));  // Output: 19
    }
}

```
#### C++ Implementation
```cpp
#include <iostream>
#include <vector>
#include <stdexcept>
using namespace std;

int sumMaxMinSecondLargest(const vector<int>& arr) {
    if (arr.size() < 2) {
        throw invalid_argument("Invalid Input");
    }

    int max = arr[0], min = arr[0], secondMax = arr[0];

    for (int num : arr) {
        if (num > max) {
            secondMax = max;
            max = num;
        } else if (num > secondMax && num != max) {
            secondMax = num;
        }
        if (num < min) {
            min = num;
        }
    }

    return max + min + secondMax;
}

int main() {
    vector<int> arr = {5, 3, 9, 2, 8};
    cout << sumMaxMinSecondLargest(arr) << endl;  // Output: 19
    return 0;
}


```
***
***Problem Created and Solved by Ms. Veda Patil***
