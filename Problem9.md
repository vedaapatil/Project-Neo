# Maximum Profit with Stock Trading and Transaction Fee

### Problem Statement

You are given an array of integers `prices` where `prices[i]` represents the price of a stock on the `i-th` day. You are also given an integer `fee` representing a transaction fee for each buy and sell. You may complete as many transactions as you like (i.e., buy one and sell one share of the stock multiple times), but you need to pay the transaction fee for each transaction. Your task is to find the maximum profit you can achieve under these conditions.
The required values are:
```
prices = [1, 3, 2, 8, 4, 9]
fee = 2
```

### Tags

```Dynamic Programming```  ```Greedy```  ```Combinatorial Optimization``` 

### Explanation

To solve this problem, we use dynamic programming to track two states for each day: 
1. The maximum profit if holding a stock.
2. The maximum profit if not holding a stock.

### Solution
```
8
```
### Pseudocode

```text
FUNCTION max_profit(prices, fee):
    n = length of prices
    IF n == 0:
        RETURN 0

    Initialize dp arrays: hold and cash
    hold[0] = -prices[0]
    cash[0] = 0

    FOR i FROM 1 TO n-1:
        hold[i] = max(hold[i-1], cash[i-1] - prices[i])
        cash[i] = max(cash[i-1], hold[i-1] + prices[i] - fee)

    RETURN cash[n-1]
```

### Implementation

#### Python Implementation
```python
def max_profit(prices, fee):
    if not prices:
        return 0

    n = len(prices)
    hold = [-prices[0]] * n
    cash = [0] * n

    for i in range(1, n):
        hold[i] = max(hold[i - 1], cash[i - 1] - prices[i])
        cash[i] = max(cash[i - 1], hold[i - 1] + prices[i] - fee)

    return cash[-1]

# Example usage
prices = [1, 3, 2, 8, 4, 9]
fee = 2
print(max_profit(prices, fee))  # Output should be 8
```
#### Java Implementation
```java
public class MaxProfitStockTrading {
    public static int maxProfit(int[] prices, int fee) {
        if (prices.length == 0) return 0;

        int n = prices.length;
        int[] hold = new int[n];
        int[] cash = new int[n];

        hold[0] = -prices[0];
        cash[0] = 0;

        for (int i = 1; i < n; i++) {
            hold[i] = Math.max(hold[i - 1], cash[i - 1] - prices[i]);
            cash[i] = Math.max(cash[i - 1], hold[i - 1] + prices[i] - fee);
        }

        return cash[n - 1];
    }

    public static void main(String[] args) {
        int[] prices = {1, 3, 2, 8, 4, 9};
        int fee = 2;
        System.out.println(maxProfit(prices, fee));  // Output should be 8
    }
}
```
#### C++ Implementation
```cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

int maxProfit(vector<int>& prices, int fee) {
    if (prices.empty()) return 0;

    int n = prices.size();
    vector<int> hold(n, 0), cash(n, 0);

    hold[0] = -prices[0];
    cash[0] = 0;

    for (int i = 1; i < n; i++) {
        hold[i] = max(hold[i - 1], cash[i - 1] - prices[i]);
        cash[i] = max(cash[i - 1], hold[i - 1] + prices[i] - fee);
    }

    return cash[n - 1];
}

int main() {
    vector<int> prices = {1, 3, 2, 8, 4, 9};
    int fee = 2;
    cout << maxProfit(prices, fee) << endl;  // Output should be 8
    return 0;
}
```
***
***Problem Created and Solved by Ms. Veda Patil***
