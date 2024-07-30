# Dual-Base Palindrome Sum

### Problem Statement

A number is called a dual-base palindrome if it is palindromic in both base 10 and base 3. For
example, 121 is a dual-base palindrome because it reads the same forwards and backwards in both
decimal and ternary. Find the sum of all numbers less than 500,000 that are palindromic in both base
10 and base 3.

### Tags

```DualBasePalindrome```  ```BaseConversion```  ```Mathematics```




### Explanation

Find numbers below 500,000 that are palindromic in both decimal and ternary (base 3). Compute the sum of such numbers.
### Solution
```
5050
```
### Pseudocode

```text

Initialize sum to 0

For n from 1 to 499999:
    If n is palindromic in base 10:
        Convert n to base 3
        If the base 3 representation is palindromic:
            Add n to sum

Return sum

```

### Implementation

#### Python Implementation
```python
def is_palindromic(s):
    return s == s[::-1]

def to_base_3(num):
    if num == 0:
        return "0"
    base3 = ""
    while num > 0:
        base3 = str(num % 3) + base3
        num //= 3
    return base3

def sum_dual_base_palindromes(limit):
    total_sum = 0
    for n in range(1, limit):
        if is_palindromic(str(n)) and is_palindromic(to_base_3(n)):
            total_sum += n
    return total_sum

print(sum_dual_base_palindromes(500000))

    
   
```
#### Java Implementation
```java

 public class DualBasePalindromes {
    public static void main(String[] args) {
        System.out.println(sumDualBasePalindromes(500000));
    }

    public static int sumDualBasePalindromes(int limit) {
        int totalSum = 0;
        for (int n = 1; n < limit; n++) {
            if (isPalindromic(Integer.toString(n)) && isPalindromic(toBase3(n))) {
                totalSum += n;
            }
        }
        return totalSum;
    }

    public static boolean isPalindromic(String s) {
        return s.equals(new StringBuilder(s).reverse().toString());
    }

    public static String toBase3(int num) {
        if (num == 0) return "0";
        StringBuilder base3 = new StringBuilder();
        while (num > 0) {
            base3.insert(0, num % 3);
            num /= 3;
        }
        return base3.toString();
    }
}
   
 
```
#### C++ Implementation
```cpp

#include <iostream>
#include <string>
using namespace std;

bool isPalindromic(const string& s) {
    int n = s.size();
    for (int i = 0; i < n / 2; ++i) {
        if (s[i] != s[n - 1 - i]) return false;
    }
    return true;
}

string toBase3(int num) {
    if (num == 0) return "0";
    string base3 = "";
    while (num > 0) {
        base3 = char(num % 3 + '0') + base3;
        num /= 3;
    }
    return base3;
}

int sumDualBasePalindromes(int limit) {
    int totalSum = 0;
    for (int n = 1; n < limit; ++n) {
        string decimalStr = to_string(n);
        if (isPalindromic(decimalStr) && isPalindromic(toBase3(n))) {
            totalSum += n;
        }
    }
    return totalSum;
}

int main() {
    cout << sumDualBasePalindromes(500000) << endl;
    return 0;
}

```
***
***Problem Created and Solved by Ms. Veda Patil***
