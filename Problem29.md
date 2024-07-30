# Reversible Primes Count

### Problem Statement

A number is called a reversible prime if it is a prime number and its digits, when reversed, also form a
prime number. For example, 13 is a reversible prime because both 13 and 31 are primes. How many
reversible primes are there below 10,000?

### Tags

```ReversiblePrimes```  ```PrimeNumbers```  ```Mathematics``` 





### Explanation
Find prime numbers below 10,000. Check if their digit reversal also forms a prime number. Count such numbers.

### Solution
```
46
```
### Pseudocode

```text
Initialize count to 0

For n from 2 to 9999:
    If n is prime:
        Reverse the digits of n to form reversedNum
        If reversedNum is prime:
            Increment count

Return count


```

### Implementation

#### Python Implementation
```python
def is_prime(num):
    if num < 2:
        return False
    for i in range(2, int(num ** 0.5) + 1):
        if num % i == 0:
            return False
    return True

def count_reversible_primes(limit):
    count = 0
    for n in range(2, limit):
        if is_prime(n):
            reversed_num = int(str(n)[::-1])
            if is_prime(reversed_num):
                count += 1
    return count

print(count_reversible_primes(10000))

```
#### Java Implementation
```java

public class ReversiblePrimes {
    public static void main(String[] args) {
        System.out.println(countReversiblePrimes(10000));
    }

    public static int countReversiblePrimes(int limit) {
        int count = 0;
        for (int n = 2; n < limit; n++) {
            if (isPrime(n)) {
                int reversedNum = reverseNumber(n);
                if (isPrime(reversedNum)) {
                    count++;
                }
            }
        }
        return count;
    }

    public static boolean isPrime(int num) {
        if (num < 2) return false;
        for (int i = 2; i <= Math.sqrt(num); i++) {
            if (num % i == 0) return false;
        }
        return true;
    }

    public static int reverseNumber(int num) {
        int reversed = 0;
        while (num > 0) {
            reversed = reversed * 10 + (num % 10);
            num /= 10;
        }
        return reversed;
    }
}

```
#### C++ Implementation
```cpp

#include <iostream>
#include <cmath>
using namespace std;

bool isPrime(int num) {
    if (num < 2) return false;
    for (int i = 2; i <= sqrt(num); i++) {
        if (num % i == 0) return false;
    }
    return true;
}

int reverseNumber(int num) {
    int reversed = 0;
    while (num > 0) {
        reversed = reversed * 10 + num % 10;
        num /= 10;
    }
    return reversed;
}

int countReversiblePrimes(int limit) {
    int count = 0;
    for (int n = 2; n < limit; n++) {
        if (isPrime(n)) {
            int reversedNum = reverseNumber(n);
            if (isPrime(reversedNum)) {
                count++;
            }
        }
    }
    return count;
}

int main() {
    cout << countReversiblePrimes(10000) << endl;
    return 0;
}

```
***
***Problem Created and Solved by Ms. Veda Patil***
