# Maximizing Pandigital Concatenation

### Problem Statement

Find the largest 1 to 9 pandigital 9-digit number that can be formed as the concatenated product of
an integer with (1, 2, ..., n) where n > 1.

### Tags

``` Pandigital Numbers  ``` ``` Number Theory ``` ``` Concatenated Products ```



### Explanation

1. Concatenated Product: For a given integer x, concatenate x X 1, x X 2, ..., up to x X n.
2. Pandigital Check: Verify if the concatenated result is a 1 to 9 pandigital number (contains each
   digit from 1 to 9 exactly once).
3. Maximization: Identify the largest such 9-digit number.

### Solution

 ``` 932718654 ```

 ### Pseudocode
```text
 Initialize max_pandigital = 0

For each integer x from 1 to a reasonable upper limit:
    For each n starting from 2:
        Concatenate the products x*1, x*2, ..., x*n
        If the concatenated number has 9 digits and is pandigital:
            If it is greater than max_pandigital:
                Update max_pandigital

Return max_pandigital

```




### Implementation

#### Python Implementation
```python
def is_pandigital(number):
    s = str(number)
    return len(s) == 9 and set(s) == set('123456789')

def find_largest_pandigital():
    max_pandigital = 0
    for x in range(1, 10000):  # Reasonable upper limit for x
        concatenated_product = ''
        n = 1
        while len(concatenated_product) < 9:
            concatenated_product += str(x * n)
            n += 1
        if len(concatenated_product) == 9 and is_pandigital(concatenated_product):
            max_pandigital = max(max_pandigital, int(concatenated_product))
    return max_pandigital

print(find_largest_pandigital())

```
#### Java Implementation
```java
import java.util.*;

public class MaximizingPandigitalConcatenation {

    private static boolean isPandigital(String s) {
        return s.length() == 9 && s.chars().distinct().count() == 9 && s.chars().allMatch(ch -> ch >= '1' && ch <= '9');
    }

    private static int findLargestPandigital() {
        int maxPandigital = 0;
        for (int x = 1; x < 10000; x++) {  // Reasonable upper limit for x
            StringBuilder concatenatedProduct = new StringBuilder();
            int n = 1;
            while (concatenatedProduct.length() < 9) {
                concatenatedProduct.append(x * n);
                n++;
            }
            if (concatenatedProduct.length() == 9 && isPandigital(concatenatedProduct.toString())) {
                maxPandigital = Math.max(maxPandigital, Integer.parseInt(concatenatedProduct.toString()));
            }
        }
        return maxPandigital;
    }

    public static void main(String[] args) {
        System.out.println(findLargestPandigital());
    }
}



```
#### C++ Implementation
```cpp
#include <iostream>
#include <string>
#include <unordered_set>
#include <algorithm>

bool isPandigital(const std::string& s) {
    if (s.length() != 9) return false;
    std::unordered_set<char> digits(s.begin(), s.end());
    return digits.size() == 9 && std::all_of(s.begin(), s.end(), [](char c) { return c >= '1' && c <= '9'; });
}

int findLargestPandigital() {
    int maxPandigital = 0;
    for (int x = 1; x < 10000; ++x) {  // Reasonable upper limit for x
        std::string concatenatedProduct;
        int n = 1;
        while (concatenatedProduct.length() < 9) {
            concatenatedProduct += std::to_string(x * n);
            ++n;
        }
        if (concatenatedProduct.length() == 9 && isPandigital(concatenatedProduct)) {
            maxPandigital = std::max(maxPandigital, std::stoi(concatenatedProduct));
        }
    }
    return maxPandigital;
}

int main() {
    std::cout << findLargestPandigital() << std::endl;
    return 0;
}

```
***
***Problem Created and Solved by Ms. Veda Patil***
