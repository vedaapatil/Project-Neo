# Distinct Digits n-th Powers

### Problem Statement

Find the smallest positive integer n such that the sum of the digits of n* is exactly 27.

### Tags

```Powers```  ```Number theory```  ```Digit sum```




### Explanation

Find the smallest positive integer n such that the sum of the digits of n* equals 27.
Steps:
1. Increment n starting from 1.
2. Compute n^4
3. Check if the sum of the digits of n^4 is 27.
4. Return the smallest n that satisfies this condition.
### Solution
```
25
```
### Pseudocode

```text
initialize n to 1
while True:
    calculate n^4
    if sum of the digits of n^4 is 27:
        return n
    increment n

```

### Implementation

#### Python Implementation
```python

 def digit_sum(n):
    return sum(int(digit) for digit in str(n))

def find_smallest_n():
    n = 1
    while True:
        if digit_sum(n ** 4) == 27:
            return n
        n += 1

print(find_smallest_n())

```
#### Java Implementation
```java
public class SmallestN {

    public static int digitSum(int n) {
        int sum = 0;
        while (n != 0) {
            sum += n % 10;
            n /= 10;
        }
        return sum;
    }

    public static int findSmallestN() {
        int n = 1;
        while (true) {
            if (digitSum((int) Math.pow(n, 4)) == 27) {
                return n;
            }
            n++;
        }
    }

    public static void main(String[] args) {
        System.out.println(findSmallestN());
    }
}

       
```
#### C++ Implementation
```cpp
#include <iostream>
#include <cmath>

int digitSum(int n) {
    int sum = 0;
    while (n != 0) {
        sum += n % 10;
        n /= 10;
    }
    return sum;
}

int findSmallestN() {
    int n = 1;
    while (true) {
        if (digitSum(pow(n, 4)) == 27) {
            return n;
        }
        n++;
    }
}

int main() {
    std::cout << findSmallestN() << std::endl;
    return 0;
}

```
***
***Problem Created and Solved by Ms. Veda Patil***
