
# Longest Increasing Subsequence in a Modified Arithmetic Progression

### Problem Statement

Given an arithmetic progression (AP) of `N` integers, with the first term `a` and common difference `d`, you need to find the length of the longest increasing subsequence (LIS) that can be formed by adding or subtracting a value `k` to any element in the AP.
The required values are:
```
N = 5
a = 2
d = 3
k = 1
```

### Tags

```Arithmetic```  ```Dynamic Programming```  ```Sequences``` 

### Explanation

To solve this problem, we need to explore the possibility of either adding or subtracting `k` from each term in the AP and then determine the longest increasing subsequence that can be formed.

### Solution
```
5
```
### Pseudocode

```text
FUNCTION find_LIS_length(N, a, d, k):
    Initialize an array `terms` of size N
    FOR i FROM 0 TO N-1:
        terms[i] = a + i * d
    Initialize a list `dp` to store LIS ending at each index
    Set `max_length` to 0

    FOR i FROM 0 TO N-1:
        dp[i] = 1
        FOR j FROM 0 TO i-1:
            IF terms[i] > terms[j]:
                dp[i] = max(dp[i], dp[j] + 1)
        max_length = max(max_length, dp[i])

    RETURN max_length
```

### Implementation

#### Python Implementation
```python
def find_LIS_length(N, a, d, k):
    terms = [a + i * d for i in range(N)]
    dp = [1] * N
    max_length = 1

    for i in range(N):
        for j in range(i):
            if terms[i] > terms[j] or terms[i] - k > terms[j]:
                dp[i] = max(dp[i], dp[j] + 1)
        max_length = max(max_length, dp[i])

    return max_length

# Example usage
N = 5
a = 2
d = 3
k = 1
print(find_LIS_length(N, a, d, k))  # Output should be 5
```
#### Java Implementation
```java
public class LongestIncreasingSubsequenceAP {
    public static int findLISLength(int N, int a, int d, int k) {
        int[] terms = new int[N];
        for (int i = 0; i < N; i++) {
            terms[i] = a + i * d;
        }

        int[] dp = new int[N];
        int maxLength = 1;

        for (int i = 0; i < N; i++) {
            dp[i] = 1;
            for (int j = 0; j < i; j++) {
                if (terms[i] > terms[j] || terms[i] - k > terms[j]) {
                    dp[i] = Math.max(dp[i], dp[j] + 1);
                }
            }
            maxLength = Math.max(maxLength, dp[i]);
        }

        return maxLength;
    }

    public static void main(String[] args) {
        int N = 5;
        int a = 2;
        int d = 3;
        int k = 1;
        System.out.println(findLISLength(N, a, d, k));  // Output should be 5
    }
}
```
#### C++ Implementation
```cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

int findLISLength(int N, int a, int d, int k) {
    vector<int> terms(N);
    for (int i = 0; i < N; i++) {
        terms[i] = a + i * d;
    }

    vector<int> dp(N, 1);
    int maxLength = 1;

    for (int i = 0; i < N; i++) {
        for (int j = 0; j < i; j++) {
            if (terms[i] > terms[j] || terms[i] - k > terms[j]) {
                dp[i] = max(dp[i], dp[j] + 1);
            }
        }
        maxLength = max(maxLength, dp[i]);
    }

    return maxLength;
}

int main() {
    int N = 5;
    int a = 2;
    int d = 3;
    int k = 1;
    cout << findLISLength(N, a, d, k) << endl;  // Output should be 5

    return 0;
}
```
***
***Problem Created and Solved by Ms. Veda Patil***
