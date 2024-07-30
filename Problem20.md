# Consecutive Prime Factor Sequences

### Problem Statement

Find the first number in a sequence of four consecutive integers where each integer has exactly four
distinct prime factors.

### Tags

``` Prime Factorization ```  ``` Consecutive Numbers ``` ```Number Theory```




### Explanation
1. Prime Factorization: For each number, determine its prime factors.
2. Count Distinct Factors: Check if a number has exactly four distinct prime factors.
3. Consecutive Sequence: Identify the first sequence of four consecutive integers where each
integer has four distinct prime factors.

### Solution

 ``` 134043 ```

 ### Pseudocode
```text
Initialize current number = 2

While not found:
    Initialize count = 0
    For each number from current number to current number + 3:
        Count distinct prime factors
        If not exactly 4 distinct factors:
            Break the loop
    If all four numbers have exactly 4 distinct prime factors:
        Return current number
    Increment current number

```




### Implementation

#### Python Implementation
```python
from sympy import primefactors

def has_four_distinct_prime_factors(num):
    return len(set(primefactors(num))) == 4

def find_first_of_sequence(length):
    current = 2
    while True:
        if all(has_four_distinct_prime_factors(current + i) for i in range(length)):
            return current
        current += 1

print(find_first_of_sequence(4))

```
#### Java Implementation
```java
import java.util.*;
import java.util.stream.Collectors;
import java.util.stream.IntStream;

public class ConsecutivePrimeFactorSequences {

    private static Set<Integer> primeFactors(int num) {
        Set<Integer> factors = new HashSet<>();
        for (int i = 2; i <= num / 2; i++) {
            while (num % i == 0) {
                factors.add(i);
                num /= i;
            }
        }
        if (num > 1) factors.add(num);
        return factors;
    }

    private static boolean hasFourDistinctPrimeFactors(int num) {
        return primeFactors(num).size() == 4;
    }

    public static int findFirstOfSequence(int length) {
        int current = 2;
        while (true) {
            boolean allHaveFourFactors = IntStream.range(0, length)
                .allMatch(i -> hasFourDistinctPrimeFactors(current + i));
            if (allHaveFourFactors) {
                return current;
            }
            current++;
        }
    }

    public static void main(String[] args) {
        System.out.println(findFirstOfSequence(4));
    }
}



```
#### C++ Implementation
```cpp

  #include <iostream>
#include <set>
#include <vector>

std::set<int> primeFactors(int num) {
    std::set<int> factors;
    for (int i = 2; i <= num / 2; ++i) {
        while (num % i == 0) {
            factors.insert(i);
            num /= i;
        }
    }
    if (num > 1) factors.insert(num);
    return factors;
}

bool hasFourDistinctPrimeFactors(int num) {
    return primeFactors(num).size() == 4;
}

int findFirstOfSequence(int length) {
    int current = 2;
    while (true) {
        bool allHaveFourFactors = true;
        for (int i = 0; i < length; ++i) {
            if (!hasFourDistinctPrimeFactors(current + i)) {
                allHaveFourFactors = false;
                break;
            }
        }
        if (allHaveFourFactors) {
            return current;
        }
        ++current;
    }
}

int main() {
    std::cout << findFirstOfSequence(4) << std::endl;
    return 0;
}

```
***
***Problem Created and Solved by Ms. Veda Patil***
