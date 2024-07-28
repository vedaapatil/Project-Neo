# Summing Primes with an Upper Bound Constraint

### Explanation

To solve this problem, we need to first generate all prime numbers less than ten thousand and store them in an array. Then, starting from the 4th index of the prime array, we sum the subsequent prime numbers until the sum is just less than one thousand. We need to implement this solution in Python, Java, and C++.

### Solution

```
946
```

### Steps:

1. **Generate Prime Numbers Less than 10,000:**
    - Use the Sieve of Eratosthenes or a simple primality test.
    - Store these prime numbers in a list.

2. **Sum Primes Starting from the 4th Index:**
    - Initialize a sum variable to 0.
    - Iterate through the list starting from the 4th index.
    - Keep adding primes to the sum until adding another prime would exceed 1000.

### Pseudocode:

```text
FUNCTION is_prime(n):
    IF n <= 1:
        RETURN False
    FOR i FROM 2 TO sqrt(n) + 1:
        IF n MOD i == 0:
            RETURN False
    RETURN True

INITIALIZE primes TO empty list

FOR i FROM 2 TO 10000:
    IF is_prime(i):
        ADD i TO primes

INITIALIZE sum_primes TO 0
INITIALIZE index TO 4

WHILE sum_primes + primes[index] < 1000:
    sum_primes = sum_primes + primes[index]
    index = index + 1

RETURN sum_primes
```

### Solution

##### Python Implementation
``` python
def is_prime(n):
    if n <= 1:
        return False
    for i in range(2, int(n**0.5) + 1):
        if n % i == 0:
            return False
    return True

# Generate all primes less than 10,000
primes = [i for i in range(10000) if is_prime(i)]

# Sum primes starting from the 4th index
sum_primes = 0
index = 4
while sum_primes + primes[index] < 1000:
    sum_primes += primes[index]
    index += 1

print(sum_primes)
```
#### Java Implementation
``` java
import java.util.ArrayList;

public class PrimeSum {
    public static void main(String[] args) {
        ArrayList<Integer> primes = new ArrayList<>();
        
        // Generate all primes less than 10,000
        for (int i = 2; i < 10000; i++) {
            if (isPrime(i)) {
                primes.add(i);
            }
        }
        
        // Sum primes starting from the 4th index
        int sumPrimes = 0;
        int index = 4;
        while (sumPrimes + primes.get(index) < 1000) {
            sumPrimes += primes.get(index);
            index++;
        }
        
        System.out.println(sumPrimes);
    }

    public static boolean isPrime(int n) {
        if (n <= 1) return false;
        for (int i = 2; i <= Math.sqrt(n); i++) {
            if (n % i == 0) return false;
        }
        return true;
    }
}
```
#### C++ Implementation
``` cpp
#include <iostream>
#include <vector>
#include <cmath>

bool isPrime(int n) {
    if (n <= 1) return false;
    for (int i = 2; i <= std::sqrt(n); i++) {
        if (n % i == 0) return false;
    }
    return true;
}

int main() {
    std::vector<int> primes;

    // Generate all primes less than 10,000
    for (int i = 2; i < 10000; i++) {
        if (isPrime(i)) {
            primes.push_back(i);
        }
    }

    // Sum primes starting from the 4th index
    int sumPrimes = 0;
    int index = 4;
    while (sumPrimes + primes[index] < 1000) {
        sumPrimes += primes[index];
        index++;
    }

    std::cout << sumPrimes << std::endl;

    return 0;
}
```
***
***Problem Created and Solved by Ms. Veda Patil***
