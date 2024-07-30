# Prime Family Generator

### Problem Statement

Find the smallest prime number that, by replacing one or more non-adjacent digits with the same
digit, is part of an eight-prime family. The family consists of all primes generated by replacing these
digits.
### Tags

``` Prime Numbers ```  ``` Digit Replacement ``` ```Prime Family```  ```Number Theory```





### Explanation
1. Generate Primes: Identify a list of prime numbers.
2. Digit Replacement: For each prime number, generate all possible numbers by replacing one or
more non-adjacent digits with the same digit.
3. Check Primes: Count how many of these generated numbers are primes.
4. Find Family: Identify the smallest prime that is part of an eight-prime family.

### Solution

 ``` 120103 ```

 ### Pseudocode
```text
 Generate a list of primes up to a reasonable limit

For each prime number:
    For each possible non-adjacent digit replacement pattern:
        Generate numbers by replacing the digits with the same digit
        Count how many of these numbers are prime
        If the count is 8:
            Return the smallest prime in this family

```




### Implementation

#### Python Implementation
```python
from sympy import isprime, primerange
from itertools import combinations

def generate_primes(limit):
    return list(primerange(2, limit))

def count_family(prime, digits_to_replace):
    prime_str = str(prime)
    family = set()
    for digit in '0123456789':
        for positions in combinations(digits_to_replace, len(digits_to_replace)):
            new_prime = list(prime_str)
            for pos in positions:
                new_prime[pos] = digit
            new_prime_str = ''.join(new_prime)
            if new_prime_str[0] != '0' and isprime(int(new_prime_str)):
                family.add(int(new_prime_str))
    return len(family)

def find_smallest_prime_family(prime_limit, family_size):
    primes = generate_primes(prime_limit)
    for prime in primes:
        prime_str = str(prime)
        for length in range(1, len(prime_str)):
            for positions in combinations(range(len(prime_str)), length):
                if count_family(prime, positions) == family_size:
                    return prime
    return None

print(find_smallest_prime_family(1000000, 8))



```
#### Java Implementation
```java
import java.util.*;
import java.util.stream.IntStream;

public class PrimeFamilyGenerator {
    private static boolean isPrime(int num) {
        if (num <= 1) return false;
        for (int i = 2; i * i <= num; i++) {
            if (num % i == 0) return false;
        }
        return true;
    }

    private static List<Integer> generatePrimes(int limit) {
        List<Integer> primes = new ArrayList<>();
        for (int num = 2; num < limit; num++) {
            if (isPrime(num)) primes.add(num);
        }
        return primes;
    }

    private static int countFamily(int prime, List<Integer> positions) {
        String primeStr = Integer.toString(prime);
        Set<Integer> family = new HashSet<>();
        for (char digit = '0'; digit <= '9'; digit++) {
            for (int[] pos : combinations(positions, positions.size())) {
                StringBuilder newPrime = new StringBuilder(primeStr);
                for (int p : pos) {
                    newPrime.setCharAt(p, digit);
                }
                String newPrimeStr = newPrime.toString();
                if (newPrimeStr.charAt(0) != '0' && isPrime(Integer.parseInt(newPrimeStr))) {
                    family.add(Integer.parseInt(newPrimeStr));
                }
            }
        }
        return family.size();
    }

    private static List<int[]> combinations(List<Integer> elements, int size) {
        // Method to generate combinations of elements with the given size
        // Implementation omitted for brevity
    }

    public static int findSmallestPrimeFamily(int primeLimit, int familySize) {
        List<Integer> primes = generatePrimes(primeLimit);
        for (int prime : primes) {
            String primeStr = Integer.toString(prime);
            for (int length = 1; length < primeStr.length(); length++) {
                for (List<Integer> positions : combinations(IntStream.range(0, primeStr.length()).boxed().collect(Collectors.toList()), length)) {
                    if (countFamily(prime, positions) == familySize) {
                        return prime;
                    }
                }
            }
        }
        return -1;
    }

    public static void main(String[] args) {
        System.out.println(findSmallestPrimeFamily(1000000, 8));
    }
}

```
#### C++ Implementation
```cpp

#include <iostream>
#include <vector>
#include <set>
#include <cmath>
#include <string>

bool isPrime(int num) {
    if (num <= 1) return false;
    for (int i = 2; i <= std::sqrt(num); ++i) {
        if (num % i == 0) return false;
    }
    return true;
}

std::vector<int> generatePrimes(int limit) {
    std::vector<int> primes;
    for (int num = 2; num < limit; ++num) {
        if (isPrime(num)) primes.push_back(num);
    }
    return primes;
}

std::set<int> generateFamily(int prime, const std::vector<int>& positions) {
    std::string primeStr = std::to_string(prime);
    std::set<int> family;
    for (char digit = '0'; digit <= '9'; ++digit) {
        for (const auto& pos : positions) {
            std::string newPrime = primeStr;
            for (int p : pos) {
                newPrime[p] = digit;
            }
            if (newPrime[0] != '0' && isPrime(std::stoi(newPrime))) {
                family.insert(std::stoi(newPrime));
            }
        }
    }
    return family;
}

int findSmallestPrimeFamily(int primeLimit, int familySize) {
    auto primes = generatePrimes(primeLimit);
    for (int prime : primes) {
        std::string primeStr = std::to_string(prime);
        for (int length = 1; length < primeStr.length(); ++length) {
            // Generate combinations of positions
            for (const auto& positions : combinations(primeStr.length(), length)) {
                if (generateFamily(prime, positions).size() == familySize) {
                    return prime;
                }
            }
        }
    }
    return -1;
}

int main() {
    std::cout << findSmallestPrimeFamily(1000000, 8) << std::endl;
    return 0;
}


```
***
***Problem Created and Solved by Ms. Veda Patil***