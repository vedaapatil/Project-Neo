# Compute the last ten digits of a series sum and the sum of numbers under 1,000,000 equal to the sum of the cubes of their digits.

### Problem Statement

Find the last ten digits of the sum of a series where each term is the sum of the cubes of the digits
from 1 to n for n up to 1000, and the sum of all numbers under 1,000,000 that are equal to the sum
of the cubes of their digits.


### Tags

```Mathematics```  ```Number Theory```  ```Algorithms```  ```Modular Arithmetic```   ```Programming``` 

### Explanation

1. Series Sum Calculation:
    • For each n from 1 to 1000, calculate the sum of cubes of the digits for all integers from 1 to
      n.
    • Accumulate these sums to get a total sum.
    • Compute the last ten digits of this total sum.
2. Sum of Special Numbers:
    • Identify numbers less than 1,000,000 that can be expressed as the sum of the cubes of their
      digits.
    • Sum these special numbers.
### Solution
```
235613701
```
### Pseudocode

```text
FUNCTION sum_of_cubes_of_digits(x)
    SET sum TO 0
    WHILE x > 0
        SET digit TO x MOD 10
        SET sum TO sum + digit^3
        SET x TO x DIV 10
    RETURN sum
END FUNCTION

FUNCTION is_sum_of_cubes_of_digits(n)
    RETURN n EQUALS sum_of_cubes_of_digits(n)
END FUNCTION

// Main Program
SET MOD TO 10000000000  // For last ten digits of the series sum
SET total_sum TO 0
SET sum_of_valid_numbers TO 0

// Task 1: Calculate Last Ten Digits of the Series Sum
FOR n FROM 1 TO 1000
    SET current_sum TO 0
    FOR i FROM 1 TO n
        SET current_sum TO current_sum + sum_of_cubes_of_digits(i)
    END FOR
    SET total_sum TO (total_sum + current_sum) MOD MOD
END FOR

OUTPUT "Last ten digits of the series sum: " + total_sum

// Task 2: Find Sum of All Numbers Less Than 1,000,000 that are Sum of Cubes of Their Digits
FOR num FROM 1 TO 999999
    IF is_sum_of_cubes_of_digits(num)
        SET sum_of_valid_numbers TO sum_of_valid_numbers + num
    END IF
END FOR

OUTPUT "Sum of all numbers that are the sum of the cubes of their digits: " + sum_of_valid_numbers

```

### Implementation

#### Python Implementation
```python
def sum_of_cubes_of_digits(x):
    return sum(int(digit) ** 3 for digit in str(x))

def is_sum_of_cubes_of_digits(n):
    return n == sum_of_cubes_of_digits(n)

# Task 1
MOD = 10**10  # For last ten digits
total_sum = 0

for n in range(1, 1001):
    current_sum = sum(sum_of_cubes_of_digits(i) for i in range(1, n+1))
    total_sum = (total_sum + current_sum) % MOD

last_ten_digits = total_sum

# Task 2
sum_of_valid_numbers = 0
for num in range(1, 1000000):
    if is_sum_of_cubes_of_digits(num):
        sum_of_valid_numbers += num

# Print results
print(f"Last ten digits of the series sum: {last_ten_digits}")
print(f"Sum of all numbers that are the sum of the cubes of their digits: {sum_of_valid_numbers}") # Output should be 235613701
```
#### Java Implementation
```java
public class SumOfCubes {

    public static int sumOfCubesOfDigits(int x) {
        int sum = 0;
        while (x > 0) {
            int digit = x % 10;
            sum += digit * digit * digit;
            x /= 10;
        }
        return sum;
    }

    public static boolean isSumOfCubesOfDigits(int n) {
        return n == sumOfCubesOfDigits(n);
    }

    public static void main(String[] args) {
        final long MOD = 10000000000L; // Use long for MOD
        long totalSum = 0;

        // Task 1
        for (int n = 1; n <= 1000; n++) {
            long currentSum = 0;
            for (int i = 1; i <= n; i++) {
                currentSum += sumOfCubesOfDigits(i);
            }
            totalSum = (totalSum + currentSum) % MOD;
        }

        long lastTenDigits = totalSum;

        // Task 2
        long sumOfValidNumbers = 0;
        for (int num = 1; num < 1000000; num++) {
            if (isSumOfCubesOfDigits(num)) {
                sumOfValidNumbers += num;
            }
        }

        // Print results
        System.out.println("Last ten digits of the series sum: " + lastTenDigits);
        System.out.println("Sum of all numbers that are the sum of the cubes of their digits: " + sumOfValidNumbers);    // Output should be 235613701
    }
}

 
    

```
#### C++ Implementation
```cpp
#include <iostream>
#include <cmath>

int sum_of_cubes_of_digits(int x) {
    int sum = 0;
    while (x > 0) {
        int digit = x % 10;
        sum += digit * digit * digit;
        x /= 10;
    }
    return sum;
}

bool is_sum_of_cubes_of_digits(int n) {
    return n == sum_of_cubes_of_digits(n);
}

int main() {
    const long long MOD = 10000000000LL;
    long long total_sum = 0;

    // Task 1
    for (int n = 1; n <= 1000; n++) {
        long long current_sum = 0;
        for (int i = 1; i <= n; i++) {
            current_sum += sum_of_cubes_of_digits(i);
        }
        total_sum = (total_sum + current_sum) % MOD;
    }

    long long last_ten_digits = total_sum;

    // Task 2
    long long sum_of_valid_numbers = 0;
    for (int num = 1; num < 1000000; num++) {
        if (is_sum_of_cubes_of_digits(num)) {
            sum_of_valid_numbers += num;
        }
    }

    // Print results
    std::cout << "Last ten digits of the series sum: " << last_ten_digits << std::endl;
    std::cout << "Sum of all numbers that are the sum of the cubes of their digits: " << sum_of_valid_numbers << std::endl;

    return 0;     // Output should be 235613701
}

```
***
***Problem Created and Solved by Ms. Veda Patil***
