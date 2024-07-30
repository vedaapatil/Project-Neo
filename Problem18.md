# Numerical Name Scoring


### Problem Statement

Using a list of numbers, where each number corresponds to a unique word in alphabetical order, calculate a numerical score for each word. The score of each word is computed by summing the positions of its digits, then multiplying this sum by the word's position in the sorted list. Find the total of all such scores.

### Tags

```File Processing```  ```Alphabetical Calculations```  ```Name Scoring``` ```Number to Word Conversion```




### Explanation

1. Convert Numbers to Words: Assume you have a file containing a list of numbers. Convert each
number to its corresponding word (e.g., 1 → "ONE", 2 → "TWO", etc.).
2. Sort Words Alphabetically: Sort the words in alphabetical order.
3. Calculate Numerical Values: For each word, compute the sum of the positions of its digits (e.g.,
"ONE" → 15 + 14 + 5 = 34).
4. Compute Name Scores: Multiply this sum by the word's position in the sorted list.
5. Calculate the Total Score: Sum up all the individual scores to get the total.
### Solution
```
4621
```
### Pseudocode

```text
Load numbers from file
Convert each number to its word representation
Sort the list of words alphabetically

Initialize total_score = 0

For each word in the sorted list:
    Compute the sum of the positions of its digits
    Compute the score for this word (position * sum)
    Add the score to total_score

Return total_score

```

### Implementation

#### Python Implementation
```python
def number_to_word(num):
    words = ["ZERO", "ONE", "TWO", "THREE", "FOUR", "FIVE", "SIX", "SEVEN", "EIGHT", "NINE"]
    return words[num]

def word_value(word):
    return sum(ord(char) - ord('A') + 1 for char in word)

def total_name_scores(file_path):
    with open(file_path, 'r') as file:
        numbers = [int(num.strip()) for num in file]
    
    words = [number_to_word(num) for num in numbers]
    words.sort()
    
    total_score = 0
    for index, word in enumerate(words):
        word_sum = word_value(word)
        total_score += (index + 1) * word_sum
    
    return total_score

print(total_name_scores('numbers.txt'))

  
  
```
#### Java Implementation
```java
import java.nio.file.*;
import java.io.IOException;
import java.util.*;

public class NumericalNameScoring {
    private static String numberToWord(int num) {
        String[] words = {"ZERO", "ONE", "TWO", "THREE", "FOUR", "FIVE", "SIX", "SEVEN", "EIGHT", "NINE"};
        return words[num];
    }

    private static int wordValue(String word) {
        int sum = 0;
        for (char c : word.toCharArray()) {
            sum += c - 'A' + 1;
        }
        return sum;
    }

    public static long totalNameScores(String filePath) throws IOException {
        List<String> lines = Files.readAllLines(Paths.get(filePath));
        List<Integer> numbers = new ArrayList<>();
        for (String line : lines) {
            numbers.add(Integer.parseInt(line.trim()));
        }

        List<String> words = new ArrayList<>();
        for (int num : numbers) {
            words.add(numberToWord(num));
        }

        Collections.sort(words);

        long totalScore = 0;
        for (int i = 0; i < words.size(); i++) {
            String word = words.get(i);
            int wordSum = wordValue(word);
            totalScore += (i + 1) * wordSum;
        }

        return totalScore;
    }

    public static void main(String[] args) throws IOException {
        System.out.println(totalNameScores("numbers.txt"));
    }
}

```
#### C++ Implementation
```cpp
#include <iostream>
#include <fstream>
#include <vector>
#include <algorithm>
#include <string>

std::string numberToWord(int num) {
    const std::string words[] = {"ZERO", "ONE", "TWO", "THREE", "FOUR", "FIVE", "SIX", "SEVEN", "EIGHT", "NINE"};
    return words[num];
}

int wordValue(const std::string& word) {
    int sum = 0;
    for (char c : word) {
        sum += c - 'A' + 1;
    }
    return sum;
}

long long totalNameScores(const std::string& filePath) {
    std::ifstream file(filePath);
    std::vector<int> numbers;
    int num;
    while (file >> num) {
        numbers.push_back(num);
    }

    std::vector<std::string> words;
    for (int number : numbers) {
        words.push_back(numberToWord(number));
    }

    std::sort(words.begin(), words.end());

    long long totalScore = 0;
    for (size_t i = 0; i < words.size(); ++i) {
        int wordSum = wordValue(words[i]);
        totalScore += (i + 1) * wordSum;
    }

    return totalScore;
}

int main() {
    std::cout << totalNameScores("numbers.txt") << std::endl;
    return 0;
}


```
***
***Problem Created and Solved by Ms. Veda Patil***
