# Pandigital Concatenation Challenge

### Problem Statement

Find the largest 1 to 9 pandigital number that can be formed as the concatenated product of an
integer x with a sequence of integers (1, 2, ...,n) where n > 1.

### Tags

``` Pandigital ```  ```Concatenated Product``` ```Number Theory``` 


### Explanation

To solve this problem, we need to:
1. Generate concatenated products of an integer x with sequences (1, 2, ..., n).
2. Check if the resulting number is a 1 to 9 pandigital number (i.e., contains each digit from 1 to 9
exactly once).
3. Keep track of the largest pandigital number found.
4. 
### Solution

 ```918273645 ```

 ### Pseudocode
```text
 Initialize max_pandigital = 0

For each integer x from 1 to 9999:
    For each n from 2 to 9:
        Generate the concatenated product of x with (1, 2, ..., n)
        If the concatenated product is a 1 to 9 pandigital number:
            If the concatenated product is greater than max_pandigital:
                Update max_pandigital

Return max_pandigital

```




### Implementation

#### Python Implementation
```python


def is_pandigital(num):
    return ''.join(sorted(str(num))) == '123456789'

def largest_pandigital():
    max_pandigital = 0
    for x in range(1, 10000):
        concatenated_product = ''
        for n in range(1, 10):
            concatenated_product += str(x * n)
            if len(concatenated_product) >= 9:
                break
        if len(concatenated_product) == 9 and is_pandigital(concatenated_product):
            max_pandigital = max(max_pandigital, int(concatenated_product))
    return max_pandigital

print(largest_pandigital())


```
#### Java Implementation
```java

public class PandigitalConcatenation {
    public static boolean isPandigital(String num) {
        return num.chars().sorted().distinct().count() == 9 && num.equals("123456789");
    }

    public static int largestPandigital() {
        int maxPandigital = 0;
        for (int x = 1; x < 10000; x++) {
            StringBuilder concatenatedProduct = new StringBuilder();
            for (int n = 1; n < 10; n++) {
                concatenatedProduct.append(x * n);
                if (concatenatedProduct.length() >= 9) {
                    break;
                }
            }
            if (concatenatedProduct.length() == 9 && isPandigital(concatenatedProduct.toString())) {
                maxPandigital = Math.max(maxPandigital, Integer.parseInt(concatenatedProduct.toString()));
            }
        }
        return maxPandigital;
    }

    public static void main(String[] args) {
        System.out.println(largestPandigital());
    }
}



```
#### C++ Implementation
```cpp
#include <iostream>
#include <string>
#include <algorithm>

bool isPandigital(const std::string &num) {
    if (num.length() != 9) return false;
    std::string sorted_num = num;
    std::sort(sorted_num.begin(), sorted_num.end());
    return sorted_num == "123456789";
}

int largestPandigital() {
    int maxPandigital = 0;
    for (int x = 1; x < 10000; ++x) {
        std::string concatenatedProduct;
        for (int n = 1; n < 10; ++n) {
            concatenatedProduct += std::to_string(x * n);
            if (concatenatedProduct.length() >= 9) break;
        }
        if (concatenatedProduct.length() == 9 && isPandigital(concatenatedProduct)) {
            maxPandigital = std::max(maxPandigital, std::stoi(concatenatedProduct));
        }
    }
    return maxPandigital;
}

int main() {
    std::cout << largestPandigital() << std::endl;
    return 0;
}

```
***
***Problem Created and Solved by Ms. Veda Patil***
