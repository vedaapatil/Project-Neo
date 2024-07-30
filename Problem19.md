# Permutational Prime Sequences


### Problem Statement
Find the 12-digit number formed by concatenating the three terms of a 4-digit arithmetic sequence, where each term is a prime number, and all terms are permutations of one another.

### Tags

```Prime Numbers```  ```Arithmetic Sequences```  ```Permutations``` 


### Explanation

1. Identify Prime Permutations: Find all 4-digit prime numbers.
2. Form Arithmetic Sequences: Check which of these primes can form an arithmetic sequence.
3. Verify Permutations: Ensure that the terms of the sequence are permutations of each other.
4. Concatenate Terms: Concatenate the three terms of the valid sequence to form a 12-digit
   number.


### Solution
```
296962999629
```
### Pseudocode

```text
Generate all 4-digit prime numbers

For each prime number, find all permutations of it
    Check if any of these permutations are prime numbers
    Form arithmetic sequences with these permutations
    If a valid sequence is found:
        Verify if it is an arithmetic sequence
        Check that all terms are permutations of each other
        Concatenate the three terms

Return the 12-digit concatenated number


```

### Implementation

#### Python Implementation
```python

  from itertools import permutations
from sympy import isprime

def generate_primes(start, end):
    return [num for num in range(start, end) if isprime(num)]

def find_arithmetic_sequence(primes):
    prime_set = set(primes)
    for p in primes:
        for q in primes:
            if q <= p:
                continue
            r = 2 * q - p
            if r in prime_set and sorted(str(p)) == sorted(str(q)) == sorted(str(r)):
                return int(f"{p}{q}{r}")

def main():
    primes = generate_primes(1000, 10000)
    result = find_arithmetic_sequence(primes)
    return result

print(main())

  
  
```
#### Java Implementation
```java
import java.util.*;
import java.util.stream.Collectors;

public class PermutationalPrimeSequences {
    private static boolean isPrime(int num) {
        if (num <= 1) return false;
        for (int i = 2; i * i <= num; i++) {
            if (num % i == 0) return false;
        }
        return true;
    }

    private static List<Integer> generatePrimes(int start, int end) {
        List<Integer> primes = new ArrayList<>();
        for (int num = start; num < end; num++) {
            if (isPrime(num)) primes.add(num);
        }
        return primes;
    }

    private static boolean isPermutation(int a, int b) {
        return (sortDigits(a).equals(sortDigits(b)));
    }

    private static String sortDigits(int num) {
        char[] digits = Integer.toString(num).toCharArray();
        Arrays.sort(digits);
        return new String(digits);
    }

    private static long findArithmeticSequence(List<Integer> primes) {
        Set<Integer> primeSet = new HashSet<>(primes);
        for (int p : primes) {
            for (int q : primes) {
                if (q <= p) continue;
                int r = 2 * q - p;
                if (primeSet.contains(r) && isPermutation(p, q) && isPermutation(q, r)) {
                    return Long.parseLong("" + p + q + r);
                }
            }
        }
        return -1;
    }

    public static void main(String[] args) {
        List<Integer> primes = generatePrimes(1000, 10000);
        System.out.println(findArithmeticSequence(primes));
    }
}


```
#### C++ Implementation
```cpp
#include <iostream>
#include <vector>
#include <set>
#include <algorithm>
#include <cmath>

bool isPrime(int num) {
    if (num <= 1) return false;
    for (int i = 2; i <= std::sqrt(num); ++i) {
        if (num % i == 0) return false;
    }
    return true;
}

std::vector<int> generatePrimes(int start, int end) {
    std::vector<int> primes;
    for (int num = start; num < end; ++num) {
        if (isPrime(num)) primes.push_back(num);
    }
    return primes;
}

std::string sortDigits(int num) {
    std::string str = std::to_string(num);
    std::sort(str.begin(), str.end());
    return str;
}

bool isPermutation(int a, int b) {
    return sortDigits(a) == sortDigits(b);
}

long long findArithmeticSequence(const std::vector<int>& primes) {
    std::set<int> primeSet(primes.begin(), primes.end());
    for (int p : primes) {
        for (int q : primes) {
            if (q <= p) continue;
            int r = 2 * q - p;
            if (primeSet.find(r) != primeSet.end() && isPermutation(p, q) && isPermutation(q, r)) {
                return std::stoll(std::to_string(p) + std::to_string(q) + std::to_string(r));
            }
        }
    }
    return -1;
}

int main() {
    std::vector<int> primes = generatePrimes(1000, 10000);
    std::cout << findArithmeticSequence(primes) << std::endl;
    return 0;
}


```
***
***Problem Created and Solved by Ms. Veda Patil***
