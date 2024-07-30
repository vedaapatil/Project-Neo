# Shortest Sum of Primes with Prime Differences

### Problem Statement

Find the lowest sum of a set of five primes such that the absolute difference between any two primes in the set is also a prime. Return the sum.

### Tags

```Prime numbers```  ```Number theory```  ```Combinatorics``` 




### Explanation

• The set should consist of five prime numbers.
• For any two primes pi and pj in the set, pi - Pj| must be prime.
• The sum of these five primes should be the lowest possible.
### Solution
```
43
```
### Pseudocode

```text
initialize list of prime numbers up to a certain limit
set min_sum to infinity

for each combination of 5 primes in the list:
    valid_combination = True
    
    for each pair of primes in the combination:
        if the absolute difference between the pair is not a prime:
            valid_combination = False
            break
    
    if valid_combination:
        current_sum = sum of the primes in the combination
        if current_sum < min_sum:
            min_sum = current_sum

return min_sum

```

### Implementation

#### Python Implementation
```python

import itertools

def is_prime(n):
    if n <= 1:
        return False
    if n <= 3:
        return True
    if n % 2 == 0 or n % 3 == 0:
        return False
    i = 5
    while i * i <= n:
        if n % i == 0 or n % (i + 2) == 0:
            return False
        i += 6
    return True

def generate_primes(limit):
    primes = []
    for num in range(2, limit):
        if is_prime(num):
            primes.append(num)
    return primes

def find_lowest_sum_of_primes():
    primes = generate_primes(100)
    min_sum = float('inf')
    
    for combination in itertools.combinations(primes, 5):
        valid_combination = True
        for i in range(5):
            for j in range(i + 1, 5):
                if not is_prime(abs(combination[i] - combination[j])):
                    valid_combination = False
                    break
            if not valid_combination:
                break
        if valid_combination:
            current_sum = sum(combination)
            if current_sum < min_sum:
                min_sum = current_sum
                
    return min_sum

print(find_lowest_sum_of_primes())

```
#### Java Implementation
```java
import java.util.ArrayList;
import java.util.List;

public class PrimeDifference {

    public static boolean isPrime(int n) {
        if (n <= 1) return false;
        if (n <= 3) return true;
        if (n % 2 == 0 || n % 3 == 0) return false;
        for (int i = 5; i * i <= n; i += 6) {
            if (n % i == 0 || n % (i + 2) == 0) return false;
        }
        return true;
    }

    public static List<Integer> generatePrimes(int limit) {
        List<Integer> primes = new ArrayList<>();
        for (int num = 2; num < limit; num++) {
            if (isPrime(num)) {
                primes.add(num);
            }
        }
        return primes;
    }

    public static int findLowestSumOfPrimes() {
        List<Integer> primes = generatePrimes(100);
        int minSum = Integer.MAX_VALUE;
        
        for (int i = 0; i < primes.size(); i++) {
            for (int j = i + 1; j < primes.size(); j++) {
                for (int k = j + 1; k < primes.size(); k++) {
                    for (int l = k + 1; l < primes.size(); l++) {
                        for (int m = l + 1; m < primes.size(); m++) {
                            int p1 = primes.get(i);
                            int p2 = primes.get(j);
                            int p3 = primes.get(k);
                            int p4 = primes.get(l);
                            int p5 = primes.get(m);
                            if (isPrime(Math.abs(p1 - p2)) && isPrime(Math.abs(p1 - p3)) && 
                                isPrime(Math.abs(p1 - p4)) && isPrime(Math.abs(p1 - p5)) &&
                                isPrime(Math.abs(p2 - p3)) && isPrime(Math.abs(p2 - p4)) &&
                                isPrime(Math.abs(p2 - p5)) && isPrime(Math.abs(p3 - p4)) &&
                                isPrime(Math.abs(p3 - p5)) && isPrime(Math.abs(p4 - p5))) {
                                int currentSum = p1 + p2 + p3 + p4 + p5;
                                if (currentSum < minSum) {
                                    minSum = currentSum;
                                }
                            }
                        }
                    }
                }
            }
        }
        return minSum;
    }

    public static void main(String[] args) {
        System.out.println(findLowestSumOfPrimes());
    }
}

```
#### C++ Implementation
```cpp
#include <iostream>
#include <vector>
#include <cmath>
#include <algorithm>

bool isPrime(int n) {
    if (n <= 1) return false;
    if (n <= 3) return true;
    if (n % 2 == 0 || n % 3 == 0) return false;
    for (int i = 5; i * i <= n; i += 6) {
        if (n % i == 0 || n % (i + 2) == 0) return false;
    }
    return true;
}

std::vector<int> generatePrimes(int limit) {
    std::vector<int> primes;
    for (int num = 2; num < limit; num++) {
        if (isPrime(num)) {
            primes.push_back(num);
        }
    }
    return primes;
}

int findLowestSumOfPrimes() {
    std::vector<int> primes = generatePrimes(100);
    int minSum = INT_MAX;

    for (size_t i = 0; i < primes.size(); i++) {
        for (size_t j = i + 1; j < primes.size(); j++) {
            for (size_t k = j + 1; k < primes.size(); k++) {
                for (size_t l = k + 1; l < primes.size(); l++) {
                    for (size_t m = l + 1; m < primes.size(); m++) {
                        int p1 = primes[i];
                        int p2 = primes[j];
                        int p3 = primes[k];
                        int p4 = primes[l];
                        int p5 = primes[m];
                        if (isPrime(abs(p1 - p2)) && isPrime(abs(p1 - p3)) && 
                            isPrime(abs(p1 - p4)) && isPrime(abs(p1 - p5)) &&
                            isPrime(abs(p2 - p3)) && isPrime(abs(p2 - p4)) &&
                            isPrime(abs(p2 - p5)) && isPrime(abs(p3 - p4)) &&
                            isPrime(abs(p3 - p5)) && isPrime(abs(p4 - p5))) {
                            int currentSum = p1 + p2 + p3 + p4 + p5;
                            if (currentSum < minSum) {
                                minSum = currentSum;
                            }
                        }
                    }
                }
            }
        }
    }
    return minSum;
}

int main() {
    std::cout << findLowestSumOfPrimes() << std::endl;
    return 0;
}

```
***
***Problem Created and Solved by Ms. Veda Patil***
