# Maximizing Right-Angle Triangle Solutions

### Problem Statement

Given a perimeter p of a right-angle triangle with integer side lengths {a, b, c}, where a + b +
c = p, determine the value of p (with p < 1000) that has the maximum number of solutions.

### Tags

```Geometry```  ``` Number Theory```  ```Combinatorial Optimization``` 

### Explanation

We need to find the perimeter p less than 1000 that can form the maximum number of distinct right-
angle triangles with integral sides. This involves iterating through possible perimeters and counting
the number of valid right-angle triangle combinations for each.
### Solution
```
840
```
### Pseudocode

```text
function count_solutions(p):
    count = 0
    for a from 1 to p // 2:
        for b from a to p // 2:
            c = p - a - b
            if a^2 + b^2 == c^2:
                count += 1
    return count

function find_max_solutions(max_p):
    max_count = 0
    best_p = 0
    for p in range(1, max_p):
        solutions = count_solutions(p)
        if solutions > max_count:
            max_count = solutions
            best_p = p
    return best_p

```

### Implementation

#### Python Implementation
```python
def count_solutions(p):
    count = 0
    for a in range(1, p // 2):
        for b in range(a, p // 2):
            c = p - a - b
            if a * a + b * b == c * c:
                count += 1
    return count

def find_max_solutions(max_p):
    max_count = 0
    best_p = 0
    for p in range(1, max_p):
        solutions = count_solutions(p)
        if solutions > max_count:
            max_count = solutions
            best_p = p
    return best_p

print(find_max_solutions(1000))

```
#### Java Implementation
```java
public class RightAngleTriangles {

    public static int countSolutions(int p) {
        int count = 0;
        for (int a = 1; a < p / 2; a++) {
            for (int b = a; b < p / 2; b++) {
                int c = p - a - b;
                if (a * a + b * b == c * c) {
                    count++;
                }
            }
        }
        return count;
    }

    public static int findMaxSolutions(int maxP) {
        int maxCount = 0;
        int bestP = 0;
        for (int p = 1; p < maxP; p++) {
            int solutions = countSolutions(p);
            if (solutions > maxCount) {
                maxCount = solutions;
                bestP = p;
            }
        }
        return bestP;
    }

    public static void main(String[] args) {
        System.out.println(findMaxSolutions(1000));
    }
}

```
#### C++ Implementation
```cpp
#include <iostream>
using namespace std;

int countSolutions(int p) {
    int count = 0;
    for (int a = 1; a < p / 2; a++) {
        for (int b = a; b < p / 2; b++) {
            int c = p - a - b;
            if (a * a + b * b == c * c) {
                count++;
            }
        }
    }
    return count;
}

int findMaxSolutions(int maxP) {
    int maxCount = 0;
    int bestP = 0;
    for (int p = 1; p < maxP; p++) {
        int solutions = countSolutions(p);
        if (solutions > maxCount) {
            maxCount = solutions;
            bestP = p;
        }
    }
    return bestP;
}

int main() {
    cout << findMaxSolutions(1000) << endl;
    return 0;
}

```
***
***Problem Created and Solved by Ms. Veda Patil***
