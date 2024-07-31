# Coin Partition Divisibility



### Problem Statement

Let p(n) represent the number of different ways in which n coins can be separated into piles. For
example, five coins can be separated into piles in exactly seven different ways, so p(5) = 7.
Find the least value of n for which p(n) is divisible by one million.
### Tags

```Combinatorial Number Theory```   

### Explanation

We need to find the smallest n such that the partition function p(n) is divisible by one million. The
partition function p(n) represents the number of ways n can be written as a sum of positive
integers, disregarding order.
### Solution
```
55374
```
### Pseudocode

```text
function partition(n):
    Initialize an array partitions with size (n+1) filled with 0
    partitions[0] = 1
    
    for i from 1 to n:
        for j from i to n:
            partitions[j] += partitions[j - i]
    
    return partitions[n]

function find_least_value_divisible_by_million():
    n = 1
    while true:
        if partition(n) % 1000000 == 0:
            return n
        n += 1

```

### Implementation

#### Python Implementation
```python
def partition(n):
    partitions = [0] * (n + 1)
    partitions[0] = 1
    for i in range(1, n + 1):
        for j in range(i, n + 1):
            partitions[j] += partitions[j - i]
    return partitions[n]

def find_least_value_divisible_by_million():
    n = 1
    while True:
        if partition(n) % 1000000 == 0:
            return n
        n += 1

print(find_least_value_divisible_by_million())

```
#### Java Implementation
```java
public class CoinPartition {
    public static int partition(int n) {
        int[] partitions = new int[n + 1];
        partitions[0] = 1;
        for (int i = 1; i <= n; i++) {
            for (int j = i; j <= n; j++) {
                partitions[j] += partitions[j - i];
            }
        }
        return partitions[n];
    }

    public static int findLeastValueDivisibleByMillion() {
        int n = 1;
        while (true) {
            if (partition(n) % 1000000 == 0) {
                return n;
            }
            n++;
        }
    }

    public static void main(String[] args) {
        System.out.println(findLeastValueDivisibleByMillion());
    }
}

```
#### C++ Implementation
```cpp
#include <iostream>
#include <vector>
using namespace std;

int partition(int n) {
    vector<int> partitions(n + 1, 0);
    partitions[0] = 1;
    for (int i = 1; i <= n; i++) {
        for (int j = i; j <= n; j++) {
            partitions[j] += partitions[j - i];
        }
    }
    return partitions[n];
}

int findLeastValueDivisibleByMillion() {
    int n = 1;
    while (true) {
        if (partition(n) % 1000000 == 0) {
            return n;
        }
        n++;
    }
}

int main() {
    cout << findLeastValueDivisibleByMillion() << endl;
    return 0;
}

```
***
***Problem Created and Solved by Ms. Veda Patil***
