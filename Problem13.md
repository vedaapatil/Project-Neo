# Find Largest Prime Sum and Permutation Primes

### Problem Statement

Find the largest prime number below one million that can be expressed as the sum of the most
consecutive prime numbers. Also, find the longest sequence of three 4-digit primes that are
permutations of each other. Concatenate these primes to form a 12-digit number. Add this number
to the largest prime found. What is the final result?

### Tags

```Prime Numbers```  ```Arithmetic Sequences```  ```Permutations``` ```Concatenation``` 




### Explanation

1. Find the largest prime below one million that can be written as the sum of consecutive
primes.
2. Identify the longest sequence of three 4-digit primes that are permutations of one another.
3. Concatenate these three primes into a 12-digit number.
4. Add this 12-digit number to the largest prime found in step 1.
### Solution
```
148749175780
```
### Pseudocode

```text
1. Find the largest prime below one million as a sum of consecutive primes:
  • Generate a list of primes below one million.
  • Iterate over possible starting primes and compute sums of consecutive primes.
  • Track the longest sum that is prime.
2. Find the longest sequence of three 4-digit primes that are permutations:
  • Generate a list of 4-digit primes.
  • Check all combinations of three primes to see if they are permutations of each other.
  • Track the sequence with the longest concatenated result.
3. Compute the final result:
  • Add the 12-digit concatenated number from step 2 to the prime found in step 1.
```

### Implementation

#### Python Implementation
```python
from sympy import primerange, isprime
from itertools import permutations

# Function to find the largest prime below limit that is a sum of consecutive primes
def find_largest_prime_sum(limit):
    primes = list(primerange(2, limit))
    max_length, result_prime = 0, 0
    
    for i in range(len(primes)):
        for j in range(i + max_length, len(primes)):
            sum_primes = sum(primes[i:j])
            if sum_primes >= limit:
                break
            if isprime(sum_primes):
                if (j - i) > max_length:
                    max_length = j - i
                    result_prime = sum_primes
    return result_prime

# Function to find the longest sequence of three permutation primes
def find_permutation_primes():
    four_digit_primes = [p for p in primerange(1000, 10000)]
    prime_set = set(four_digit_primes)
    longest_concat = 0
    
    for p1 in four_digit_primes:
        for p2 in four_digit_primes:
            if p1 < p2 and sorted(str(p1)) == sorted(str(p2)):
                for p3 in four_digit_primes:
                    if p1 < p3 and p2 < p3 and sorted(str(p1)) == sorted(str(p3)):
                        concat_number = int(f"{p1}{p2}{p3}")
                        if concat_number > longest_concat:
                            longest_concat = concat_number
    return longest_concat

# Main computation
limit = 1000000
largest_prime_sum = find_largest_prime_sum(limit)
longest_concat_prime = find_permutation_primes()
final_result = largest_prime_sum + longest_concat_prime

print(final_result)   

```
#### Java Implementation
```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.HashSet;
import java.util.List;
import java.util.Set;

public class PrimeSequences {
    
    // Check if a number is prime
    public static boolean isPrime(int num) {
        if (num <= 1) return false;
        if (num == 2 || num == 3) return true;
        if (num % 2 == 0 || num % 3 == 0) return false;
        for (int i = 5; i * i <= num; i += 6) {
            if (num % i == 0 || num % (i + 2) == 0) return false;
        }
        return true;
    }
    
    // Generate a list of primes below the given limit
    public static List<Integer> generatePrimes(int limit) {
        List<Integer> primes = new ArrayList<>();
        for (int i = 2; i < limit; i++) {
            if (isPrime(i)) primes.add(i);
        }
        return primes;
    }
    
    // Find the largest prime that is a sum of consecutive primes
    public static int findLargestPrimeSum(int limit) {
        List<Integer> primes = generatePrimes(limit);
        int maxLength = 0;
        int resultPrime = 0;

        for (int i = 0; i < primes.size(); i++) {
            int sumPrimes = 0;
            for (int j = i; j < primes.size(); j++) {
                sumPrimes += primes.get(j);
                if (sumPrimes >= limit) break;
                if (isPrime(sumPrimes) && (j - i + 1) > maxLength) {
                    maxLength = j - i + 1;
                    resultPrime = sumPrimes;
                }
            }
        }
        return resultPrime;
    }
    
    // Find the longest sequence of three permutation primes
    public static int findPermutationPrimes() {
        List<Integer> primes = new ArrayList<>();
        for (int i = 1000; i < 10000; i++) {
            if (isPrime(i)) primes.add(i);
        }
        
        int longestConcat = 0;
        
        for (int i = 0; i < primes.size(); i++) {
            for (int j = i + 1; j < primes.size(); j++) {
                if (isPermutation(primes.get(i), primes.get(j))) {
                    for (int k = j + 1; k < primes.size(); k++) {
                        if (isPermutation(primes.get(i), primes.get(k))) {
                            int concatNumber = Integer.parseInt(String.valueOf(primes.get(i)) + primes.get(j) + primes.get(k));
                            if (concatNumber > longestConcat) {
                                longestConcat = concatNumber;
                            }
                        }
                    }
                }
            }
        }
        return longestConcat;
    }
    
   

```
#### C++ Implementation
```cpp
#include <iostream>
#include <vector>
#include <algorithm>
#include <cmath>
#include <unordered_set>

bool isPrime(int num) {
    if (num <= 1) return false;
    if (num == 2 || num == 3) return true;
    if (num % 2 == 0 || num % 3 == 0) return false;
    for (int i = 5; i * i <= num; i += 6) {
        if (num % i == 0 || num % (i + 2) == 0) return false;
    }
    return true;
}

std::vector<int> generatePrimes(int limit) {
    std::vector<int> primes;
    for (int i = 2; i < limit; ++i) {
        if (isPrime(i)) primes.push_back(i);
    }
    return primes;
}

int findLargestPrimeSum(int limit) {
    std::vector<int> primes = generatePrimes(limit);
    int max_length = 0, result_prime = 0;

    for (size_t i = 0; i < primes.size(); ++i) {
        int sum_primes = 0;
        for (size_t j = i; j < primes.size(); ++j) {
            sum_primes += primes[j];
            if (sum_primes >= limit) break;
            if (isPrime(sum_primes) && (j - i + 1) > max_length) {
                max_length = j - i + 1;
                result_prime = sum_primes;
            }
        }
    }
    return result_prime;
}

int findPermutationPrimes() {
    std::vector<int> primes;
    for (int i = 1000; i < 10000; ++i) {
        if (isPrime(i)) primes.push_back(i);
    }

    int longest_concat = 0;

    for (size_t i = 0; i < primes.size(); ++i) {
        for (size_t j = i + 1; j < primes.size(); ++j) {
            if (std::is_permutation(std::to_string(primes[i]).begin(), std::to_string(primes[i]).end(),
                                    std::to_string(primes[j]).begin())) {
                for (size_t k = j + 1; k < primes.size(); ++k) {
                    if (std::is_permutation(std::to_string(primes[i]).begin(), std::to_string(primes[i]).end(),
                                            std::to_string(primes[k]).begin())) {
                        int concat_number = std::stoi(std::to_string(primes[i]) + std::to_string(primes[j]) + std::to_string(primes[k]));
                        if (concat_number > longest_concat) {
                            longest_concat = concat_number;
                        }
                    }
                }
            }
        }
    }
    return longest_concat;
}

int main() {
    int limit = 1000000;
    int largest_prime_sum = findLargestPrimeSum(limit);
    int longest_concat_prime = findPermutationPrimes();
    int final_result = largest_prime_sum + longest_concat_prime;

    std::cout << final_result << std::endl;
    return 0;
}

```
***
***Problem Created and Solved by Ms. Veda Patil***
