# Second Largest Prime in a Range

### Problem Statement

Write a function to find the second largest prime number within a given range of integers.

### Tags

```Prime Numbers```  ```Range```  ``` Second Largest```  ```List Generation```  

### Explanation

This combines generating prime numbers within a range and finding the second largest prime number.


### Solution
```
43
```
### Pseudocode

```text


function generatePrimesInRange(start, end):
    primes = []
    for num from start to end:
        if isPrime(num):
            primes.append(num)
    return primes

function isPrime(num):
    if num <= 1:
        return false
    for i from 2 to sqrt(num):
        if num % i == 0:
            return false
    return true

function secondLargestPrime(start, end):
    primes = generatePrimesInRange(start, end)
    if length of primes < 2:
        return "Not enough primes"
    return primes[length of primes - 2]

```

### Implementation

#### Python Implementation
```python
import math

def is_prime(num):
    if num <= 1:
        return False
    for i in range(2, int(math.sqrt(num)) + 1):
        if num % i == 0:
            return False
    return True

def generate_primes_in_range(start, end):
    return [num for num in range(start, end + 1) if is_prime(num)]

def second_largest_prime(start, end):
    primes = generate_primes_in_range(start, end)
    if len(primes) < 2:
        return "Not enough primes"
    return primes[-2]

# Sample Input
start = 10
end = 50
print(second_largest_prime(start, end))  # Output: 43

```
#### Java Implementation
```java

 import java.util.ArrayList;
import java.util.List;

public class SecondLargestPrimeInRange {
    public static boolean isPrime(int num) {
        if (num <= 1) return false;
        for (int i = 2; i <= Math.sqrt(num); i++) {
            if (num % i == 0) return false;
        }
        return true;
    }

    public static List<Integer> generatePrimesInRange(int start, int end) {
        List<Integer> primes = new ArrayList<>();
        for (int num = start; num <= end; num++) {
            if (isPrime(num)) primes.add(num);
        }
        return primes;
    }

    public static int secondLargestPrime(int start, int end) {
        List<Integer> primes = generatePrimesInRange(start, end);
        if (primes.size() < 2) {
            throw new IllegalArgumentException("Not enough primes");
        }
        return primes.get(primes.size() - 2);
    }

    public static void main(String[] args) {
        int start = 10;
        int end = 50;
        System.out.println(secondLargestPrime(start, end));  // Output: 43
    }
}

 
    

```
#### C++ Implementation
```cpp
#include <iostream>
#include <vector>
#include <cmath>
using namespace std;

bool isPrime(int num) {
    if (num <= 1) return false;
    for (int i = 2; i <= sqrt(num); i++) {
        if (num % i == 0) return false;
    }
    return true;
}

vector<int> generatePrimesInRange(int start, int end) {
    vector<int> primes;
    for (int num = start; num <= end; num++) {
        if (isPrime(num)) primes.push_back(num);
    }
    return primes;
}

int secondLargestPrime(int start, int end) {
    vector<int> primes = generatePrimesInRange(start, end);
    if (primes.size() < 2) {
        throw invalid_argument("Not enough primes");
    }
    return primes[primes.size() - 2];
}

int main() {
    int start = 10;
    int end = 50;
    cout << secondLargestPrime(start, end) << endl;  // Output: 43
    return 0;
}

```
***
***Problem Created and Solved by Ms. Veda Patil***
