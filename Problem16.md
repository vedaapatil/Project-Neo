# Sum of Diagonal Numbers in a 1001x1001 Spiral with Incremented Values

### Problem Statement
Given a 1001 by 1001 spiral, what is the sum of the numbers on the diagonals if every number in the spiral is increased by 5?

### Tags

```Mathematics```  ```Spiral```  ```DiagonalSum``` ```ArithmeticSequence``` ```Algorithm``` 

### Explanation

1. **Spiral Formation:**
     - The spiral starts with 1 at the center and moves to the right in a clockwise direction.
     - For any n x n spiral (where n is odd), the diagonals contain numbers that form arithmetic
        sequences.
2. **Diagonal Sums Calculation:**
    - For a 1001 × 1001 spiral, the diagonals include the sequence of corner values at each
     layer.
    - For each layer k (starting from the center), the corner values can be calculated using the
      formula for the top-right corner of each layer, then adjusted for other corners.
3. **Modification:**
    - Each number in the spiral is increased by 5.
    - Hence, the sum of the numbers on the diagonals will be the sum of the original spiral
      diagonal numbers plus 5 times the count of numbers on the diagonals.
      
### Solution
```

```
### Pseudocode

```text
function diagonal_sum_modified(n):
    if n % 2 == 0:
        return "n must be odd"
    
    original_sum = 1
    current_number = 1
    
    for layer in range(1, (n // 2) + 1):
        step = 2 * layer
        for _ in range(4):
            current_number += step
            original_sum += current_number
    
    total_numbers_on_diagonals = 2 * n - 1
    modified_sum = original_sum + 5 * total_numbers_on_diagonals
    
    return modified_sum

n = 1001
print(diagonal_sum_modified(n))

```

### Implementation

#### Python Implementation
```python
def diagonal_sum_modified(n):
    if n % 2 == 0:
        return "n must be odd"
    
    original_sum = 1
    current_number = 1
    
    for layer in range(1, (n // 2) + 1):
        step = 2 * layer
        for _ in range(4):
            current_number += step
            original_sum += current_number
    
    total_numbers_on_diagonals = 2 * n - 1
    modified_sum = original_sum + 5 * total_numbers_on_diagonals
    
    return modified_sum

n = 1001
print(diagonal_sum_modified(n))
```
#### Java Implementation
```java
public class SpiralDiagonalSum {
    public static int diagonalSumModified(int n) {
        if (n % 2 == 0) {
            throw new IllegalArgumentException("n must be odd");
        }
        
        int originalSum = 1;
        int currentNumber = 1;
        
        for (int layer = 1; layer <= n / 2; layer++) {
            int step = 2 * layer;
            for (int i = 0; i < 4; i++) {
                currentNumber += step;
                originalSum += currentNumber;
            }
        }
        
        int totalNumbersOnDiagonals = 2 * n - 1;
        int modifiedSum = originalSum + 5 * totalNumbersOnDiagonals;
        
        return modifiedSum;
    }

    public static void main(String[] args) {
        int n = 1001;
        System.out.println(diagonalSumModified(n));
    }
}

```
#### C++ Implementation
```cpp

#include <iostream>
using namespace std;

int diagonalSumModified(int n) {
    if (n % 2 == 0) {
        throw invalid_argument("n must be odd");
    }
    
    int originalSum = 1;
    int currentNumber = 1;
    
    for (int layer = 1; layer <= n / 2; layer++) {
        int step = 2 * layer;
        for (int i = 0; i < 4; i++) {
            currentNumber += step;
            originalSum += currentNumber;
        }
    }
    
    int totalNumbersOnDiagonals = 2 * n - 1;
    int modifiedSum = originalSum + 5 * totalNumbersOnDiagonals;
    
    return modifiedSum;
}

int main() {
    int n = 1001;
    cout << diagonalSumModified(n) << endl;
    return 0;
}

```
***
***Problem Created and Solved by Ms. Veda Patil***
