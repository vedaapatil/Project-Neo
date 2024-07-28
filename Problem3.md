## For the first 100 triangular numbers, find the one that has the largest difference between the sum of the squares of its divisors and the square of the sum of its divisors. Calculate the difference for each triangular number and determine which one has the largest difference.

### Problem Statement

Find a triangular number In is generated by adding the natural numbers up to n and can be expressed
as Tn = n(R+1).
For the first 100 triangular numbers, find the triangular number that has the largest difference
between the sum of the squares of its divisors and the square of the sum of its divisors.


### Tags

```Triangular Numbers``` ```Divisors``` ```Number Theory``` ```Sum of Squares``` ```Mathematical Difference```


### Explanation
To solve this problem, we need to find the triangular number among the first 100 triangular numbers
that has the largest difference between the sum of the squares of its divisors and the square of the
sum of its divisors. We need to implement this solution in Python, Java, and C++.



### Solution

```
4560
```

### Steps:

1. **Generate Triangular Numbers:**
    - The triangular number for n is calculated using the formula T, = 1(2+2).
2. **Find Divisors:**
    - For each triangular number, find all its divisors.
3. **Sum of Squares of Divisors:**
    - Calculate the sum of the squares of the divisors.
4. **Square of Sum of Divisors:**
    - Calculate the square of the sum of the divisors.
5. **Find the Difference:**
    - Calculate the difference between the square of the sum and the sum of the squares of the
   divisors.
    - Track the maximum difference and the corresponding triangular number.
### Pseudocode:

```text
FUNCTION sum_of_squares_of_divisors(n):
    sum_of_squares = 0
    FOR i FROM 1 TO sqrt(n):
        IF n MOD i == 0:
            sum_of_squares = sum_of_squares + i * i
            IF i != n / i:
                sum_of_squares = sum_of_squares + (n / i) * (n / i)
    RETURN sum_of_squares

FUNCTION sum_of_divisors(n):
    sum = 0
    FOR i FROM 1 TO sqrt(n):
        IF n MOD i == 0:
            sum = sum + i
            IF i != n / i:
                sum = sum + n / i
    RETURN sum

INITIALIZE max_difference TO 0
INITIALIZE max_difference_triangular_number TO 0

FOR n FROM 1 TO 100:
    triangular_number = n * (n + 1) / 2
    sum_squares = sum_of_squares_of_divisors(triangular_number)
    sum = sum_of_divisors(triangular_number)
    square_of_sum = sum * sum
    difference = square_of_sum - sum_squares
    IF difference > max_difference:
        max_difference = difference
        max_difference_triangular_number = triangular_number

RETURN max_difference_triangular_number

```

### Solution

##### Python Implementation
``` python
import math

def sum_of_divisors(n):
    divisors = set()
    for i in range(1, int(math.sqrt(n)) + 1):
        if n % i == 0:
            divisors.add(i)
            if i != n // i:
                divisors.add(n // i)
    return list(divisors)

def main():
    max_difference = 0
    result = 0
    
    for n in range(1, 101):
        triangular_number = n * (n + 1) // 2
        divisors = sum_of_divisors(triangular_number)
        
        sum_of_squares = sum(d**2 for d in divisors)
        square_of_sum = sum(divisors)**2
        
        difference = square_of_sum - sum_of_squares
        
        if difference > max_difference:
            max_difference = difference
            result = triangular_number
    
    return result

print(main())

```
#### Java Implementation
``` java
import java.util.ArrayList;
import java.util.HashSet;
import java.util.Set;

public class TriangularNumberDifference {
    
    public static void main(String[] args) {
        System.out.println(findMaxDifferenceTriangularNumber());
    }

    public static int findMaxDifferenceTriangularNumber() {
        int maxDifference = 0;
        int result = 0;

        for (int n = 1; n <= 100; n++) {
            int triangularNumber = n * (n + 1) / 2;
            ArrayList<Integer> divisors = sumOfDivisors(triangularNumber);

            int sumOfSquares = 0;
            int sum = 0;

            for (int divisor : divisors) {
                sumOfSquares += divisor * divisor;
                sum += divisor;
            }

            int squareOfSum = sum * sum;
            int difference = squareOfSum - sumOfSquares;

            if (difference > maxDifference) {
                maxDifference = difference;
                result = triangularNumber;
            }
        }

        return result;
    }

    public static ArrayList<Integer> sumOfDivisors(int n) {
        ArrayList<Integer> divisors = new ArrayList<>();
        for (int i = 1; i <= Math.sqrt(n); i++) {
            if (n % i == 0) {
                divisors.add(i);
                if (i != n / i) {
                    divisors.add(n / i);
                }
            }
        }
        return divisors;
    }
}

    
```
#### C++ Implementation
``` cpp
#include <iostream>
#include <vector>
#include <cmath>
#include <unordered_set>

using namespace std;

vector<int> sumOfDivisors(int n) {
    unordered_set<int> divisors;
    for (int i = 1; i <= sqrt(n); i++) {
        if (n % i == 0) {
            divisors.insert(i);
            if (i != n / i) {
                divisors.insert(n / i);
            }
        }
    }
    return vector<int>(divisors.begin(), divisors.end());
}

int findMaxDifferenceTriangularNumber() {
    int maxDifference = 0;
    int result = 0;

    for (int n = 1; n <= 100; n++) {
        int triangularNumber = n * (n + 1) / 2;
        vector<int> divisors = sumOfDivisors(triangularNumber);

        int sumOfSquares = 0;
        int sum = 0;

        for (int divisor : divisors) {
            sumOfSquares += divisor * divisor;
            sum += divisor;
        }

        int squareOfSum = sum * sum;
        int difference = squareOfSum - sumOfSquares;

        if (difference > maxDifference) {
            maxDifference = difference;
            result = triangularNumber;
        }
    }

    return result;
}

int main() {
    cout << findMaxDifferenceTriangularNumber() << endl;
    return 0;
}

   
```
***
***Problem Created and Solved by Ms. Veda Patil***