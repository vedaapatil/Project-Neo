# Pandigital Prime Search



### Problem Statement

A number is said to be pandigital if it uses all the digits 1 to n exactly once. For example, 2143 is a 4-
digit pandigital number and is also prime.
Find the largest n-digit pandigital number that is a prime.
### Tags

```Number Theory```  ```Pandigital Numbers```  ``` Prime Numbers``` 

### Explanation

To solve this problem, generate all pandigital numbers of varying lengths and check for primality,
starting from the largest possible pandigital number downwards.
### Solution
```
7652413
```
### Pseudocode

```text
function is_prime(num):
    if num <= 1:
        return false
    if num <= 3:
        return true
    if num % 2 == 0 or num % 3 == 0:
        return false
    i = 5
    while i * i <= num:
        if num % i == 0 or num % (i + 2) == 0:
            return false
        i += 6
    return true

function generate_pandigital_numbers(n):
    return permutations of digits 1 to n

function find_largest_pandigital_prime():
    for n from 9 down to 1:
        pandigital_numbers = generate_pandigital_numbers(n)
        for number in sorted(pandigital_numbers, reverse=True):
            if is_prime(number):
                return number

```

### Implementation

#### Python Implementation
```python
from itertools import permutations

def is_prime(num):
    if num <= 1:
        return False
    if num <= 3:
        return True
    if num % 2 == 0 or num % 3 == 0:
        return False
    i = 5
    while i * i <= num:
        if num % i == 0 or num % (i + 2) == 0:
            return False
        i += 6
    return True

def generate_pandigital_numbers(n):
    digits = ''.join(str(i) for i in range(1, n + 1))
    return [int(''.join(p)) for p in permutations(digits)]

def find_largest_pandigital_prime():
    for n in range(9, 0, -1):
        pandigital_numbers = generate_pandigital_numbers(n)
        for number in sorted(pandigital_numbers, reverse=True):
            if is_prime(number):
                return number

print(find_largest_pandigital_prime())

```
#### Java Implementation
```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

public class PandigitalPrime {

    public static boolean isPrime(long num) {
        if (num <= 1) return false;
        if (num <= 3) return true;
        if (num % 2 == 0 || num % 3 == 0) return false;
        for (long i = 5; i * i <= num; i += 6) {
            if (num % i == 0 || num % (i + 2) == 0) return false;
        }
        return true;
    }

    public static List<Long> generatePandigitalNumbers(int n) {
        List<Long> pandigitalNumbers = new ArrayList<>();
        String digits = "";
        for (int i = 1; i <= n; i++) {
            digits += i;
        }
        generatePermutations("", digits, pandigitalNumbers);
        return pandigitalNumbers;
    }

    private static void generatePermutations(String prefix, String str, List<Long> pandigitalNumbers) {
        int n = str.length();
        if (n == 0) {
            pandigitalNumbers.add(Long.parseLong(prefix));
        } else {
            for (int i = 0; i < n; i++) {
                generatePermutations(prefix + str.charAt(i), str.substring(0, i) + str.substring(i + 1, n), pandigitalNumbers);
            }
        }
    }

    public static long findLargestPandigitalPrime() {
        for (int n = 9; n >= 1; n--) {
            List<Long> pandigitalNumbers = generatePandigitalNumbers(n);
            Collections.sort(pandigitalNumbers, Collections.reverseOrder());
            for (long number : pandigitalNumbers) {
                if (isPrime(number)) {
                    return number;
                }
            }
        }
        return -1; // If no pandigital prime is found, though there should be one
    }

    public static void main(String[] args) {
        System.out.println(findLargestPandigitalPrime());
    }
}

```
#### C++ Implementation
```cpp
#include <iostream>
#include <vector>
#include <algorithm>
#include <cmath>
#include <string>

using namespace std;

bool is_prime(long long num) {
    if (num <= 1) return false;
    if (num <= 3) return true;
    if (num % 2 == 0 || num % 3 == 0) return false;
    for (long long i = 5; i * i <= num; i += 6) {
        if (num % i == 0 || num % (i + 2) == 0) return false;
    }
    return true;
}

void generate_permutations(string prefix, string str, vector<long long>& pandigital_numbers) {
    int n = str.length();
    if (n == 0) {
        pandigital_numbers.push_back(stoll(prefix));
    } else {
        for (int i = 0; i < n; i++) {
            generate_permutations(prefix + str[i], str.substr(0, i) + str.substr(i + 1), pandigital_numbers);
        }
    }
}

vector<long long> generate_pandigital_numbers(int n) {
    vector<long long> pandigital_numbers;
    string digits;
    for (int i = 1; i <= n; i++) {
        digits += to_string(i);
    }
    generate_permutations("", digits, pandigital_numbers);
    return pandigital_numbers;
}

long long find_largest_pandigital_prime() {
    for (int n = 9; n >= 1; n--) {
        vector<long long> pandigital_numbers = generate_pandigital_numbers(n);
        sort(pandigital_numbers.rbegin(), pandigital_numbers.rend());
        for (long long number : pandigital_numbers) {
            if (is_prime(number)) {
                return number;
            }
        }
    }
    return -1; // If no pandigital prime is found, though there should be one
}

int main() {
    cout << find_largest_pandigital_prime() << endl;
    return 0;
}

```
***
***Problem Created and Solved by Ms. Veda Patil***
