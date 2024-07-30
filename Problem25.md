# Last Digits of Power Series Sum
### Problem Statement

Find the last ten digits of the sum of the series 11^1 + 22^2 + 33^3 + ... + 10001000^10001000

### Tags

```Modular Arithmetic```  ```Large Numbers```  ```Series Sum``` 



### Explanation

1. Series Definition: Each term in the series is kk where k ranges from 11 to 10001000.
2. Sum Computation: Calculate the sum of all terms in this series.
3. Modulo Operation: To find the last ten digits, compute the result modulo 10^10.
### Solution
```
3760959057
```
### Pseudocode

```text
Initialize total_sum = 0
MOD = 10^10

For k from 11 to 10001000:
    Compute term = k^k % MOD
    Add term to total_sum
    Apply MOD to total_sum to keep only the last ten digits

Return total_sum

```

### Implementation

#### Python Implementation
```python
def last_ten_digits_of_series(start, end):
    MOD = 10**10
    total_sum = 0

    for k in range(start, end + 1):
        term = pow(k, k, MOD)
        total_sum = (total_sum + term) % MOD

    return total_sum

print(last_ten_digits_of_series(11, 10001000))

```
#### Java Implementation
```java
  
   import java.math.BigInteger;

public class LastDigitsOfPowerSeriesSum {

    private static final BigInteger MOD = BigInteger.TEN.pow(10);

    private static BigInteger lastTenDigitsOfSeries(int start, int end) {
        BigInteger totalSum = BigInteger.ZERO;

        for (int k = start; k <= end; k++) {
            BigInteger term = BigInteger.valueOf(k).modPow(BigInteger.valueOf(k), MOD);
            totalSum = totalSum.add(term).mod(MOD);
        }

        return totalSum;
    }

    public static void main(String[] args) {
        System.out.println(lastTenDigitsOfSeries(11, 10001000));
    }
}

```
#### C++ Implementation
```cpp
#include <iostream>
#include <cmath>

const long long MOD = 10000000000LL;

long long mod_exp(long long base, long long exp, long long mod) {
    long long result = 1;
    while (exp > 0) {
        if (exp % 2 == 1) {
            result = (result * base) % mod;
        }
        base = (base * base) % mod;
        exp /= 2;
    }
    return result;
}

long long lastTenDigitsOfSeries(int start, int end) {
    long long totalSum = 0;

    for (int k = start; k <= end; ++k) {
        long long term = mod_exp(k, k, MOD);
        totalSum = (totalSum + term) % MOD;
    }

    return totalSum;
}

int main() {
    std::cout << lastTenDigitsOfSeries(11, 10001000) << std::endl;
    return 0;
}



```
***
***Problem Created and Solved by Ms. Veda Patil***
