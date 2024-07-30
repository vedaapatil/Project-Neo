# Invalid Goldbach Composite

### Problem Statement

Find the smallest odd composite number that cannot be expressed as the sum of a prime and twice
a square.

### Tags

```Goldbach’s Conjecture```  ```Composite Numbers```  ```Prime Numbers```  ```Number Theory``` 





### Explanation

1. **Odd Composite Numbers: Generate a list of odd composite numbers (numbers greater than 1
   that are not prime and not even).**
2. **Goldbach's Conjecture Check: For each odd composite number, check if it can be written as the
   sum of a prime and twice a square. Specifically, for each odd composite n:**
    - Find a prime p and an integer k such that n = p + 2k'.
3. **Find Invalid Number: Identify the smallest odd composite number that cannot be expressed in
   this form.**
### Solution
```
5777
```
### Pseudocode

```text
Generate a list of odd composite numbers

For each odd composite number:
    Set a flag indicating if it can be expressed as the sum of a prime and twice a square
    For each prime less than the number:
        For each integer k:
            Check if the number can be expressed as prime + 2 * k^2
            If found, set the flag and break
    If the flag remains unset:
        Return this odd composite number

```

### Implementation

#### Python Implementation
```python
from sympy import isprime, primerange
import math

def generate_odd_composites(limit):
    odd_composites = []
    for num in range(3, limit, 2):
        if not isprime(num):
            odd_composites.append(num)
    return odd_composites

def check_goldbach_conjecture(n):
    for p in primerange(2, n):
        k = 1
        while 2 * k * k < n:
            if p + 2 * k * k == n:
                return True
            k += 1
    return False

def find_smallest_invalid_goldbach(limit):
    odd_composites = generate_odd_composites(limit)
    for number in odd_composites:
        if not check_goldbach_conjecture(number):
            return number

print(find_smallest_invalid_goldbach(10000))

```
#### Java Implementation
```java
import java.util.*;

public class InvalidGoldbachComposite {

    private static boolean isPrime(int num) {
        if (num <= 1) return false;
        for (int i = 2; i * i <= num; i++) {
            if (num % i == 0) return false;
        }
        return true;
    }

    private static List<Integer> generateOddComposites(int limit) {
        List<Integer> oddComposites = new ArrayList<>();
        for (int num = 3; num < limit; num += 2) {
            if (!isPrime(num)) {
                oddComposites.add(num);
            }
        }
        return oddComposites;
    }

    private static boolean checkGoldbachConjecture(int n) {
        for (int p = 2; p < n; p++) {
            if (isPrime(p)) {
                int k = 1;
                while (2 * k * k < n) {
                    if (p + 2 * k * k == n) {
                        return true;
                    }
                    k++;
                }
            }
        }
        return false;
    }

    private static int findSmallestInvalidGoldbach(int limit) {
        List<Integer> oddComposites = generateOddComposites(limit);
        for (int number : oddComposites) {
            if (!checkGoldbachConjecture(number)) {
                return number;
            }
        }
        return -1;
    }

    public static void main(String[] args) {
        System.out.println(findSmallestInvalidGoldbach(10000));
    }
}

```
#### C++ Implementation
```cpp
#include <iostream>
#include <vector>
#include <cmath>
#include <algorithm>

bool isPrime(int num) {
    if (num <= 1) return false;
    for (int i = 2; i <= std::sqrt(num); ++i) {
        if (num % i == 0) return false;
    }
    return true;
}

std::vector<int> generateOddComposites(int limit) {
    std::vector<int> oddComposites;
    for (int num = 3; num < limit; num += 2) {
        if (!isPrime(num)) {
            oddComposites.push_back(num);
        }
    }
    return oddComposites;
}

bool checkGoldbachConjecture(int n) {
    for (int p = 2; p < n; ++p) {
        if (isPrime(p)) {
            int k = 1;
            while (2 * k * k < n) {
                if (p + 2 * k * k == n) {
                    return true;
                }
                ++k;
            }
        }
    }
    return false;
}

int findSmallestInvalidGoldbach(int limit) {
    auto oddComposites = generateOddComposites(limit);
    for (int number : oddComposites) {
        if (!checkGoldbachConjecture(number)) {
            return number;
        }
    }
    return -1;
}

int main() {
    std::cout << findSmallestInvalidGoldbach(10000) << std::endl;
    return 0;
}

```
***
***Problem Created and Solved by Ms. Veda Patil***
