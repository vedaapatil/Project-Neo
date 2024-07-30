# Sum of digits of a power and sum of multiples of 3 or 5

### Problem Statement

Find the sum of the digits of the number 2500, then add it to the sum of all the multiples of 3 or 5
below 1000. What is the final result?

### Tags

``` Exponentiation```  ```Digit Sum```  ```Multiples``` ```Summation``` ```Number Theory```


### Explanation

• First, calculate 2500 and find the sum of its digits.
• Second, find the sum of all natural numbers below 1000 that are multiples of 3 or 5.
• Finally, add the results of both calculations to get the final number.
### Solution
```

```
### Pseudocode

```text
1. Calculate the value of 2^500.
2. Convert the result to a string to iterate over each digit.
3. Compute the sum of the digits of 2^500.
4. Initialize sum_multiples to 0.
5. Loop over numbers from 1 to 999:
    a. If the number is divisible by 3 or 5, add it to sum_multiples.
6. Add the sum of digits of 2^500 to sum_multiples.
7. Return the final result.

```

### Implementation

#### Python Implementation
```python
# Function to calculate the sum of the digits of 2^500
def sum_of_digits_of_power(base, exponent):
    number = base ** exponent
    return sum(int(digit) for digit in str(number))

# Function to calculate the sum of multiples of 3 or 5 below a given limit
def sum_of_multiples(limit):
    return sum(x for x in range(limit) if x % 3 == 0 or x % 5 == 0)

# Calculating the sum of digits of 2^500
digit_sum = sum_of_digits_of_power(2, 500)

# Calculating the sum of multiples of 3 or 5 below 1000
multiples_sum = sum_of_multiples(1000)

# Final result
final_result = digit_sum + multiples_sum
print(final_result)

```
#### Java Implementation
```java
 import java.math.BigInteger;

public class Main {
    public static void main(String[] args) {
        // Sum of digits of 2^500
        BigInteger number = BigInteger.valueOf(2).pow(500);
        int digitSum = sumOfDigits(number.toString());

        // Sum of multiples of 3 or 5 below 1000
        int multiplesSum = sumOfMultiples(1000);

        // Final result
        int finalResult = digitSum + multiplesSum;
        System.out.println(finalResult);
    }

    private static int sumOfDigits(String number) {
        int sum = 0;
        for (char digit : number.toCharArray()) {
            sum += Character.getNumericValue(digit);
        }
        return sum;
    }

    private static int sumOfMultiples(int limit) {
        int sum = 0;
        for (int i = 1; i < limit; i++) {
            if (i % 3 == 0 || i % 5 == 0) {
                sum += i;
            }
        }
        return sum;
    }
}

```
#### C++ Implementation
```cpp
#include <iostream>
#include <cmath>
#include <string>
#include <numeric>
#include <algorithm>

using namespace std;

// Function to calculate the sum of the digits of a large number
int sumOfDigits(string number) {
    return accumulate(number.begin(), number.end(), 0, [](int sum, char digit) {
        return sum + (digit - '0');
    });
}

// Function to calculate the sum of multiples of 3 or 5 below a given limit
int sumOfMultiples(int limit) {
    int sum = 0;
    for (int i = 1; i < limit; ++i) {
        if (i % 3 == 0 || i % 5 == 0) {
            sum += i;
        }
    }
    return sum;
}

int main() {
    // Sum of digits of 2^500
    string number = to_string(static_cast<long double>(pow(2, 500)));
    int digitSum = sumOfDigits(number);

    // Sum of multiples of 3 or 5 below 1000
    int multiplesSum = sumOfMultiples(1000);

    // Final result
    int finalResult = digitSum + multiplesSum;
    cout << finalResult << endl;

    return 0;
}

```
***
***Problem Created and Solved by Ms. Veda Patil***
