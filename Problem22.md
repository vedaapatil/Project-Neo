# Permutational Multiples

### Problem Statement

Find the smallest positive integer x such that the numbers 2x, 3x, 4x, 5x, and 6x are permutations
of the digits of x.

### Tags

``` Permutations ```  ``` Multiples ``` ```Number Theory```  




### Explanation

1. Permutations Check: For each integer x, check if 2x, 3x, 4x, 5x, and 6x are permutations of
the digits of x.
2. Smallest x: Identify the smallest x that satisfies this condition.

### Solution

 ``` 142857```

 ### Pseudocode
```text
 Initialize x = 1

While true:
    For each multiplier from 2 to 6:
        Check if the digits of x and multiplier * x are permutations
    If all multipliers give permutations:
        Return x
    Increment x

```




### Implementation

#### Python Implementation
```python
from collections import Counter

def is_permutation(a, b):
    return Counter(str(a)) == Counter(str(b))

def find_smallest_permutational_integer():
    x = 1
    while True:
        if all(is_permutation(x, k*x) for k in range(2, 7)):
            return x
        x += 1

print(find_smallest_permutational_integer())


```
#### Java Implementation
```java
import java.util.*;

public class PermutationalMultiples {

    private static boolean isPermutation(int a, int b) {
        String strA = Integer.toString(a);
        String strB = Integer.toString(b);
        char[] arrA = strA.toCharArray();
        char[] arrB = strB.toCharArray();
        Arrays.sort(arrA);
        Arrays.sort(arrB);
        return Arrays.equals(arrA, arrB);
    }

    private static int findSmallestPermutationalInteger() {
        int x = 1;
        while (true) {
            boolean allMatch = true;
            for (int k = 2; k <= 6; k++) {
                if (!isPermutation(x, k * x)) {
                    allMatch = false;
                    break;
                }
            }
            if (allMatch) {
                return x;
            }
            x++;
        }
    }

    public static void main(String[] args) {
        System.out.println(findSmallestPermutationalInteger());
    }
}



```
#### C++ Implementation
```cpp
#include <iostream>
#include <algorithm>
#include <string>
#include <unordered_map>

bool isPermutation(int a, int b) {
    std::string strA = std::to_string(a);
    std::string strB = std::to_string(b);
    std::sort(strA.begin(), strA.end());
    std::sort(strB.begin(), strB.end());
    return strA == strB;
}

int findSmallestPermutationalInteger() {
    int x = 1;
    while (true) {
        bool allMatch = true;
        for (int k = 2; k <= 6; k++) {
            if (!isPermutation(x, k * x)) {
                allMatch = false;
                break;
            }
        }
        if (allMatch) {
            return x;
        }
        x++;
    }
}

int main() {
    std::cout << findSmallestPermutationalInteger() << std::endl;
    return 0;
}


```
***
***Problem Created and Solved by Ms. Veda Patil***
