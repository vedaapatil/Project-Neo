
# Maximum Sum of Distinct Subsequence in an Arithmetic Progression

### Problem Statement

Given an arithmetic progression (AP) of `N` integers, with the first term `a` and common difference `d`, you need to find the maximum sum of a subsequence such that no two elements in the subsequence are adjacent in the AP.
The required values are:
```
N = 5
a = 1
d = 3
```

### Tags

```Arithmetic```  ```Dynamic Programming```  ```Sequences``` 

### Explanation

To solve this problem, we need to identify the best strategy to select elements from the AP such that the sum is maximized and no two elements are adjacent.

### Solution
```
21
```
### Pseudocode

```text
FUNCTION max_sum_of_non_adjacent_elements(N, a, d):
    Initialize an array `dp` of size N
    Set `dp[0]` to a (first term of the AP)
    Set `dp[1]` to max(a, a + d) (either take the first element or the second)
    
    FOR i FROM 2 TO N-1:
        term = a + i * d
        dp[i] = max(dp[i-1], dp[i-2] + term)
    
    RETURN dp[N-1]
```

### Implementation

#### Python Implementation
```python
def max_sum_of_non_adjacent_elements(N, a, d):
    if N == 1:
        return a
    if N == 2:
        return max(a, a + d)

    dp = [0] * N
    dp[0] = a
    dp[1] = max(a, a + d)

    for i in range(2, N):
        term = a + i * d
        dp[i] = max(dp[i - 1], dp[i - 2] + term)

    return dp[-1]

# Example usage
N = 5
a = 1
d = 3
print(max_sum_of_non_adjacent_elements(N, a, d))  # Output should be 21
```
#### Java Implementation
```java
public class MaxSumNonAdjacentAP {
    public static int maxSumNonAdjacent(int N, int a, int d) {
        if (N == 1) return a;
        if (N == 2) return Math.max(a, a + d);

        int[] dp = new int[N];
        dp[0] = a;
        dp[1] = Math.max(a, a + d);

        for (int i = 2; i < N; i++) {
            int term = a + i * d;
            dp[i] = Math.max(dp[i - 1], dp[i - 2] + term);
        }

        return dp[N - 1];
    }

    public static void main(String[] args) {
        int N = 5;
        int a = 1;
        int d = 3;
        System.out.println(maxSumNonAdjacent(N, a, d));  // Output should be 21
    }
}
```
#### C++ Implementation
```cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

int maxSumNonAdjacent(int N, int a, int d) {
    if (N == 1) return a;
    if (N == 2) return max(a, a + d);

    vector<int> dp(N);
    dp[0] = a;
    dp[1] = max(a, a + d);

    for (int i = 2; i < N; i++) {
        int term = a + i * d;
        dp[i] = max(dp[i - 1], dp[i - 2] + term);
    }

    return dp[N - 1];
}

int main() {
    int N = 5;
    int a = 1;
    int d = 3;
    cout << maxSumNonAdjacent(N, a, d) << endl;  // Output should be 21

    return 0;
}
```
***
***Problem Created and Solved by [Your Name]***
