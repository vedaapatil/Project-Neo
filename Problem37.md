# Palindromic Mismatch Index
### Problem Statement
Find the index of the first element where a list differs from its reverse.

### Tags

```List```  ```Palindrome```  ```Reversal```  ```Index```   


### Explanation

Return the index of the first mismatch between the list and its reverse.
### Solution
```
2
```
### Pseudocode

```text
function findMismatchIndex(arr):
    reversed_arr = reverse(arr)
    
    for i from 0 to length of arr - 1:
        if arr[i] != reversed_arr[i]:
            return i
    
    return -1  # Returns -1 if no mismatch is found, meaning the list is a palindrome

```

### Implementation

#### Python Implementation
```python
def find_mismatch_index(arr):
    reversed_arr = arr[::-1]
    
    for i in range(len(arr)):
        if arr[i] != reversed_arr[i]:
            return i
    
    return -1  # -1 if the list is a palindrome

# Sample Input
arr = [1, 2, 3, 2, 1]
print(find_mismatch_index(arr))  # Output: 2

```
#### Java Implementation
```java
 public class PalindromicReversalIndex {
    public static int findMismatchIndex(int[] arr) {
        int[] reversedArr = new int[arr.length];
        
        for (int i = 0; i < arr.length; i++) {
            reversedArr[i] = arr[arr.length - 1 - i];
        }
        
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] != reversedArr[i]) {
                return i;
            }
        }
        
        return -1;  // -1 if the list is a palindrome
    }

    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 2, 1};
        System.out.println(findMismatchIndex(arr));  // Output: 2
    }
}

 
    

```
#### C++ Implementation
```cpp
 #include <iostream>
#include <vector>
using namespace std;

int findMismatchIndex(const vector<int>& arr) {
    vector<int> reversedArr(arr.rbegin(), arr.rend());
    
    for (int i = 0; i < arr.size(); i++) {
        if (arr[i] != reversedArr[i]) {
            return i;
        }
    }
    
    return -1;  // -1 if the list is a palindrome
}

int main() {
    vector<int> arr = {1, 2, 3, 2, 1};
    cout << findMismatchIndex(arr) << endl;  // Output: 2
    return 0;
}


```
***
***Problem Created and Solved by Ms. Veda Patil***
