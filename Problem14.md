# 

### Problem Statement

Find the smallest prime > 1000 that is the sum of the most consecutive integers and concatenate it
with the longest recurring cycle length of ¿ for d < 1000. What is the result?

### Tags

```Prime Numbers```  ```Consecutive Sums```  ```Recurring Decimal Cycles```




### Explanation

1. **Find the smallest prime greater than 1000 that is the sum of the most consecutive integers:**
    - Iterate through prime numbers greater than 1000.
    - For each prime, check if it can be written as the sum of consecutive integers.
    - Track the prime that can be written as the sum of the most consecutive integers.
2. **Find the longest recurring cycle in a for d < 1000:**
    - Calculate the length of the recurring cycle for each d.
    - Track the maximum cycle length.
3. **Concatenate the prime from Step 1 with the cycle length from Step 2 to form the final result.**
### Solution
```

```
### Pseudocode

```text
Function prime_consecutive_sum():
    Initialize max_terms to 0 and result_prime to None
    For prime in range 1001 to 10000:
        If prime is a prime number:
            For start in range 1 to prime:
                Initialize total to 0 and terms to 0
                For num in range start to prime:
                    Add num to total and increment terms
                    If total equals prime:
                        If terms > max_terms:
                            Update max_terms and result_prime
                        Break loop
                    If total > prime:
                        Break loop
                If total >= prime:
                    Break loop
    Return result_prime

Function cycle_length(d):
    Initialize an empty dictionary remainders
    Set value to 1 and position to 0
    While value is not 0 and value not in remainders:
        Store position in remainders with value as key
        Set value to (value * 10) % d
        Increment position
    Return position - remainders[value] if value in remainders, else 0

Function longest_recurring_cycle():
    Initialize max_cycle_length to 0
    For d in range 2 to 999:
        Calculate length using cycle_length(d)
        If length > max_cycle_length:
            Update max_cycle_length
    Return max_cycle_length

Set prime to result of prime_consecutive_sum()
Set cycle_length to result of longest_recurring_cycle()
Concatenate prime and cycle_length to form final_result
Print final_result

```

### Implementation

#### Python Implementation
```python
from sympy import isprime

def prime_consecutive_sum():
    primes = [i for i in range(1001, 10000) if isprime(i)]
    max_terms, result_prime = 0, None

    for prime in primes:
        for start in range(1, prime):
            total, terms = 0, 0
            for num in range(start, prime):
                total += num
                terms += 1
                if total == prime:
                    if terms > max_terms:
                        max_terms = terms
                        result_prime = prime
                    break
                if total > prime:
                    break
            if total >= prime:
                break
    return result_prime

def longest_recurring_cycle():
    def cycle_length(d):
        remainders = {}
        value, position = 1, 0
        while value and value not in remainders:
            remainders[value] = position
            value = (value * 10) % d
            position += 1
        return position - remainders.get(value, 0)

    max_cycle, result_d = 0, 0
    for d in range(2, 1000):
        length = cycle_length(d)
        if length > max_cycle:
            max_cycle = length
            result_d = d
    return max_cycle

prime = prime_consecutive_sum()
cycle_length = longest_recurring_cycle()
final_result = int(f"{prime}{cycle_length}")
print(final_result)

```
#### Java Implementation
```java
import java.util.*;

public class Main {

    private static boolean isPrime(int num) {
        if (num <= 1) return false;
        if (num == 2 || num == 3) return true;
        if (num % 2 == 0 || num % 3 == 0) return false;
        for (int i = 5; i * i <= num; i += 6) {
            if (num % i == 0 || num % (i + 2) == 0) return false;
        }
        return true;
    }

    private static int primeConsecutiveSum() {
        for (int prime = 1001; prime < 10000; prime++) {
            if (isPrime(prime)) {
                int maxTerms = 0;
                for (int start = 1; start < prime; start++) {
                    int sum = 0, terms = 0;
                    for (int num = start; num < prime; num++) {
                        sum += num;
                        terms++;
                        if (sum == prime) {
                            if (terms > maxTerms) {
                                maxTerms = terms;
                                return prime;
                            }
                            break;
                        }
                        if (sum > prime) break;
                    }
                    if (sum >= prime) break;
                }
            }
        }
        return 0; // Shouldn't happen
    }

    private static int longestRecurringCycle() {
        int maxCycle = 0;

        for (int d = 2; d < 1000; d++) {
            Map<Integer, Integer> remainders = new HashMap<>();
            int value = 1, position = 0;

            while (value != 0 && !remainders.containsKey(value)) {
                remainders.put(value, position);
                value = (value * 10) % d;
                position++;
            }

            int length = position - remainders.getOrDefault(value, 0);
            if (length > maxCycle) {
                maxCycle = length;
            }
        }
        return maxCycle;
    }

    public static void main(String[] args) {
        int prime = primeConsecutiveSum();
        int cycleLength = longestRecurringCycle();
        String finalResult = String.valueOf(prime) + cycleLength;
        System.out.println(finalResult);
    }
}

```
#### C++ Implementation
```cpp
#include <iostream>
#include <unordered_map>
#include <cmath>

bool isPrime(int num) {
    if (num <= 1) return false;
    if (num == 2 || num == 3) return true;
    if (num % 2 == 0 || num % 3 == 0) return false;
    for (int i = 5; i * i <= num; i += 6) {
        if (num % i == 0 || num % (i + 2) == 0) return false;
    }
    return true;
}

int primeConsecutiveSum() {
    for (int prime = 1001; prime < 10000; prime++) {
        if (isPrime(prime)) {
            int maxTerms = 0;
            for (int start = 1; start < prime; start++) {
                int sum = 0, terms = 0;
                for (int num = start; num < prime; num++) {
                    sum += num;
                    terms++;
                    if (sum == prime) {
                        if (terms > maxTerms) {
                            maxTerms = terms;
                            return prime;
                        }
                        break;
                    }
                    if (sum > prime) break;
                }
                if (sum >= prime) break;
            }
        }
    }
    return 0; // Shouldn't happen
}

int longestRecurringCycle() {
    int maxCycle = 0;

    for (int d = 2; d < 1000; d++) {
        std::unordered_map<int, int> remainders;
        int value = 1, position = 0;

        while (value != 0 && remainders.find(value) == remainders.end()) {
            remainders[value] = position;
            value = (value * 10) % d;
            position++;
        }

        int length = position - remainders[value];
        if (length > maxCycle) {
            maxCycle = length;
        }
    }
    return maxCycle;
}

int main() {
    int prime = primeConsecutiveSum();
    int cycleLength = longestRecurringCycle();
    std::cout << std::to_string(prime) + std::to_string(cycleLength) << std::endl;
    return 0;
}

```
***
***Problem Created and Solved by Ms. Veda Patil***
