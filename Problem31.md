# Prime Sum Representations

### Problem Statement

Consider the number of ways to write a given integer n as the sum of prime numbers. For example,
ten can be written as the sum of primes in exactly five different ways:
• 7 + 3
• 5 + 5
• 5 + 3 + 2
• 3+3 + 2 + 2
• 2+2+2 + 2 + 2
Determine the first integer n which can be written as the sum of prime numbers in over five
thousand different ways.
### Tags

```Combinatorial Number Theory```  

### Explanation

We need to count the number of ways to express n as a sum of prime numbers, considering
different permutations of the same set of primes as distinct.
### Solution
```
71
```
### Pseudocode

```text
function prime_sums(n):
    Initialize an array ways with size (n+1) filled with 0
    ways[0] = 1
    
    List of prime numbers less than or equal to n
    
    for each prime in primes:
        for i from prime to n:
            ways[i] += ways[i - prime]
    
    return ways[n]

function find_first_value_with_over_5000_ways():
    n = 1
    while true:
        if prime_sums(n) > 5000:
            return n
        n += 1

```

### Implementation

#### Python Implementation
```python
def sieve(limit):
    is_prime = [True] * (limit + 1)
    is_prime[0] = is_prime[1] = False
    for i in range(2, int(limit**0.5) + 1):
        if is_prime[i]:
            for j in range(i*i, limit + 1, i):
                is_prime[j] = False
    return [x for x in range(limit + 1) if is_prime[x]]

def prime_sums(n):
    primes = sieve(n)
    ways = [0] * (n + 1)
    ways[0] = 1
    for prime in primes:
        for i in range(prime, n + 1):
            ways[i] += ways[i - prime]
    return ways[n]

def find_first_value_with_over_5000_ways():
    n = 1
    while True:
        if prime_sums(n) > 5000:
            return n
        n += 1

print(find_first_value_with_over_5000_ways())

```
#### Java Implementation
```java
import java.util.ArrayList;
import java.util.List;

public class PrimeSum {
    public static List<Integer> sieve(int limit) {
        boolean[] isPrime = new boolean[limit + 1];
        for (int i = 2; i <= limit; i++) isPrime[i] = true;
        for (int i = 2; i * i <= limit; i++) {
            if (isPrime[i]) {
                for (int j = i * i; j <= limit; j += i) isPrime[j] = false;
            }
        }
        List<Integer> primes = new ArrayList<>();
        for (int i = 2; i <= limit; i++) {
            if (isPrime[i]) primes.add(i);
        }
        return primes;
    }

    public static int primeSums(int n) {
        List<Integer> primes = sieve(n);
        int[] ways = new int[n + 1];
        ways[0] = 1;
        for (int prime : primes) {
            for (int i = prime; i <= n; i++) {
                ways[i] += ways[i - prime];
            }
        }
        return ways[n];
    }

    public static int findFirstValueWithOver5000Ways() {
        int n = 1;
        while (true) {
            if (primeSums(n) > 5000) return n;
            n++;
        }
    }

    public static void main(String[] args) {
        System.out.println(findFirstValueWithOver5000Ways());
    }
}

```
#### C++ Implementation
```cpp
#include <iostream>
#include <vector>
using namespace std;

vector<int> sieve(int limit) {
    vector<bool> is_prime(limit + 1, true);
    is_prime[0] = is_prime[1] = false;
    for (int i = 2; i * i <= limit; i++) {
        if (is_prime[i]) {
            for (int j = i * i; j <= limit; j += i) {
                is_prime[j] = false;
            }
        }
    }
    vector<int> primes;
    for (int i = 2; i <= limit; i++) {
        if (is_prime[i]) {
            primes.push_back(i);
        }
    }
    return primes;
}

int primeSums(int n) {
    vector<int> primes = sieve(n);
    vector<int> ways(n + 1, 0);
    ways[0] = 1;
    for (int prime : primes) {
        for (int i = prime; i <= n; i++) {
            ways[i] += ways[i - prime];
        }
    }
    return ways[n];
}

int findFirstValueWithOver5000Ways() {
    int n = 1;
    while (true) {
        if (primeSums(n) > 5000) {
            return n;
        }
        n++;
    }
}

int main() {
    cout << findFirstValueWithOver5000Ways() << endl;
    return 0;
}

```
***
***Problem Created and Solved by Ms. Veda Patil***
