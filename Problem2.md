# Summing Palindromic Primes Less than 100,000

### Problem Statement

Find the sum of all palindromic prime numbers less than 100,000.

### Tags

```palindromes``` ```primes``` ```Primality Test Function``` ```Big Integers```

### Explanation

To solve this problem, we need to find all palindromic primes less than 100,000. A palindromic prime is a number that is both prime and reads the same forwards and backwards. Once we have identified these palindromic primes, we will sum them up to get the final result.

### Solution

```
4838098
```

### Steps:

1. **Generate Prime Numbers Less than 100,000:**
    - Use a primality test function
    - Store the prime numbers in a list

2. **Check if the Prime Numbers are Palindromic:**
    - Use a function to check if a number reads the same forwards and backwards
    - Filter the list of primes to get only palindromic primes

3. **Sum All Palindromic Primes:**
    - Sum up all the palindromic primes obtained in the previous step.

### Pseudocode:

```text
FUNCTION is_prime(n):
    IF n <= 1:
        RETURN False
    FOR i FROM 2 TO sqrt(n) + 1:
        IF n MOD i == 0:
            RETURN False
    RETURN True

FUNCTION is_palindrome(n):
    RETURN str(n) == str(n)[::-1]

INITIALIZE palindromic_primes TO empty list

FOR i FROM 2 TO 100000:
    IF is_prime(i) AND is_palindrome(i):
        ADD i TO palindromic_primes

INITIALIZE sum_palindromic_primes TO 0

FOR p IN palindromic_primes:
    sum_palindromic_primes = sum_palindromic_primes + p

RETURN sum_palindromic_primes
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

def is_palindrome(n):
    return str(n) == str(n)[::-1]

# Generate all palindromic primes less than 100,000
palindromic_primes = [i for i in range(100000) if is_prime(i) and is_palindrome(i)]

# Sum all palindromic primes
sum_palindromic_primes = sum(palindromic_primes)

print(sum_palindromic_primes)
```
#### Java Implementation
``` java
import java.util.ArrayList;

public class PalindromicPrimeSum {
    public static void main(String[] args) {
        ArrayList<Integer> palindromicPrimes = new ArrayList<>();
        
        // Generate all palindromic primes less than 100,000
        for (int i = 2; i < 100000; i++) {
            if (isPrime(i) && isPalindrome(i)) {
                palindromicPrimes.add(i);
            }
        }
        
        // Sum all palindromic primes
        int sumPalindromicPrimes = 0;
        for (int p : palindromicPrimes) {
            sumPalindromicPrimes += p;
        }
        
        System.out.println(sumPalindromicPrimes);
    }

    public static boolean isPrime(int n) {
        if (n <= 1) return false;
        for (int i = 2; i <= Math.sqrt(n); i++) {
            if (n % i == 0) return false;
        }
        return true;
    }

    public static boolean isPalindrome(int n) {
        String str = Integer.toString(n);
        return str.equals(new StringBuilder(str).reverse().toString());
    }
}
```
#### C++ Implementation
``` cpp
#include <iostream>
#include <vector>
#include <cmath>
#include <algorithm>

bool isPrime(int n) {
    if (n <= 1) return false;
    for (int i = 2; i <= std::sqrt(n); i++) {
        if (n % i == 0) return false;
    }
    return true;
}

bool isPalindrome(int n) {
    std::string str = std::to_string(n);
    std::string rev = str;
    std::reverse(rev.begin(), rev.end());
    return str == rev;
}

int main() {
    std::vector<int> palindromicPrimes;

    // Generate all palindromic primes less than 100,000
    for (int i = 2; i < 100000; i++) {
        if (isPrime(i) && isPalindrome(i)) {
            palindromicPrimes.push_back(i);
        }
    }

    // Sum all palindromic primes
    int sumPalindromicPrimes = 0;
    for (int p : palindromicPrimes) {
        sumPalindromicPrimes += p;
    }

    std::cout << sumPalindromicPrimes << std::endl;

    return 0;
}
```
***
***Problem Created and Solved by Ms. Veda Patil***
