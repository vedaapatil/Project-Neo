# Alphabetical Value Sum for Number Words

### Problem Statement

If the number 43 is written as "forty-three," and the sum of the letters' positions in the English
alphabet (where A=1, B=2, etc.) is 99, what is the sum of the positions of the letters in the English
representation of 10000?

### Tags

``` Text Processing ```  ``` String Manipulation ``` ```Alphabetical Value Calculation```  ```Number to Words Conversion```

### Explanation

To solve this problem, follow these steps:
1. Convert the number 10000 into its English word representation.
2. Calculate the sum of the positions of each letter in the English alphabet (where A=1, B=2, ...,
Z=26) for the word representation of 10000.

### Solution

 ``` 141 ```

 ### Pseudocode
```text
 FUNCTION calculate_alphabetical_sum(word):
    Initialize sum to 0
    FOR each character in the word:
        IF character is a letter:
            Convert character to lowercase
            Calculate its alphabetical position (A=1, B=2, ..., Z=26)
            Add the position to the sum
    RETURN sum

FUNCTION main():
    number = 10000
    word = convert_number_to_words(number)
    result = calculate_alphabetical_sum(word)
    PRINT result
```




### Implementation

#### Python Implementation
```python
import inflect

def letter_position_sum(word):
    sum_ = 0
    for char in word.lower():
        if char.isalpha():
            sum_ += ord(char) - ord('a') + 1
    return sum_

def convert_number_to_words(number):
    p = inflect.engine()
    return p.number_to_words(number)

def main():
    number = 10000
    word = convert_number_to_words(number)
    result = letter_position_sum(word)
    print(result)

# Example usage
main()


```
#### Java Implementation
```java
import java.text.DecimalFormat;

public class LetterPositionSum {
    public static void main(String[] args) {
        int number = 10000;
        String word = numberToWords(number);
        int result = letterPositionSum(word);
        System.out.println(result);
    }

    public static String numberToWords(int number) {
        // Implement or use a library to convert number to words
        return "ten thousand"; // Placeholder
    }

    public static int letterPositionSum(String word) {
        word = word.toLowerCase();
        int sum = 0;
        for (char c : word.toCharArray()) {
            if (Character.isLetter(c)) {
                sum += c - 'a' + 1;
            }
        }
        return sum;
    }
}


```
#### C++ Implementation
```cpp
#include <iostream>
#include <string>
#include <cctype>

// Function to convert number to words (requires implementation or library)
std::string numberToWords(int number) {
    // Stub implementation
    return "ten thousand"; // Replace with actual implementation
}

int letterPositionSum(const std::string& word) {
    int sum = 0;
    for (char c : word) {
        if (std::isalpha(c)) {
            sum += std::tolower(c) - 'a' + 1;
        }
    }
    return sum;
}

int main() {
    int number = 10000;
    std::string word = numberToWords(number);
    int result = letterPositionSum(word);
    std::cout << result << std::endl;
    return 0;
}

```
***
***Problem Created and Solved by Ms. Veda Patil***
