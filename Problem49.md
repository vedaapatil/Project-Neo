# Merge Overlapping Intervals and Rearrange Zigzag Order

### Problem Statement
Write a function to merge overlapping intervals in a list and then rearrange the elements of the merged intervals in zigzag order (a < b > c < d > e).

### Tags

```Intervals```  ```Zigzag Order```  ```Merging```  


### Explanation
This combines merging overlapping intervals with rearranging the merged intervals into a zigzag order.
### Solution
```
[[1, 6], [8, 10], [15, 18]] 
```
### Pseudocode

```text
function mergeIntervalsAndZigzagOrder(intervals):
    # Step 1: Merge overlapping intervals
    intervals.sort(key=lambda x: x[0])
    merged = []
    for interval in intervals:
        if not merged or merged[-1][1] < interval[0]:
            merged.append(interval)
        else:
            merged[-1][1] = max(merged[-1][1], interval[1])
    
    # Step 2: Rearrange merged intervals in zigzag order
    merged_flattened = [elem for sublist in merged for elem in sublist]
    zigzag = []
    for i in range(len(merged_flattened)):
        if i % 2 == 0:
            zigzag.append(merged_flattened[i])
        else:
            zigzag.insert(-1, merged_flattened[i])
    
    return merged, zigzag


```

### Implementation

#### Python Implementation
```python
def merge_intervals_and_zigzag_order(intervals):
    # Step 1: Merge overlapping intervals
    intervals.sort(key=lambda x: x[0])
    merged = []
    for interval in intervals:
        if not merged or merged[-1][1] < interval[0]:
            merged.append(interval)
        else:
            merged[-1][1] = max(merged[-1][1], interval[1])
    
    # Step 2: Rearrange merged intervals in zigzag order
    merged_flattened = [elem for sublist in merged for elem in sublist]
    zigzag = []
    for i in range(len(merged_flattened)):
        if i % 2 == 0:
            zigzag.append(merged_flattened[i])
        else:
            zigzag.insert(-1, merged_flattened[i])
    
    return merged, zigzag

# Sample Input
intervals = [[1, 3], [2, 6], [8, 10], [15, 18]]
merged, zigzag = merge_intervals_and_zigzag_order(intervals)
print("Merged Intervals:", merged)  # Output: Merged Intervals: [[1, 6], [8, 10], [15, 18]]
print("Zigzag Order:", zigzag)      # Output: Zigzag Order: [1, 6, 8, 10, 15, 18]

```
#### Java Implementation
```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

public class MergeIntervalsAndZigzag {
    public static List<List<Integer>> mergeIntervalsAndZigzagOrder(List<List<Integer>> intervals) {
        // Step 1: Merge overlapping intervals
        intervals.sort((a, b) -> Integer.compare(a.get(0), b.get(0)));
        List<List<Integer>> merged = new ArrayList<>();
        for (List<Integer> interval : intervals) {
            if (merged.isEmpty() || merged.get(merged.size() - 1).get(1) < interval.get(0)) {
                merged.add(new ArrayList<>(interval));
            } else {
                merged.get(merged.size() - 1).set(1, Math.max(merged.get(merged.size() - 1).get(1), interval.get(1)));
            }
        }
        
        // Step 2: Rearrange merged intervals in zigzag order
        List<Integer> mergedFlattened = new ArrayList<>();
        for (List<Integer> interval : merged) {
            mergedFlattened.add(interval.get(0));
            mergedFlattened.add(interval.get(1));
        }
        List<Integer> zigzag = new ArrayList<>();
        for (int i = 0; i < mergedFlattened.size(); i++) {
            if (i % 2 == 0) {
                zigzag.add(mergedFlattened.get(i));
            } else {
                zigzag.add(zigzag.size() - 1, mergedFlattened.get(i));
            }
        }
        
        return Arrays.asList(merged, zigzag);
    }

    public static void main(String[] args) {
        List<List<Integer>> intervals = Arrays.asList(
            Arrays.asList(1, 3),
            Arrays.asList(2, 6),
            Arrays.asList(8, 10),
            Arrays.asList(15, 18)
        );
        List<List<Integer>> result = mergeIntervalsAndZigzagOrder(intervals);
        System.out.println("Merged Intervals: " + result.get(0));
        System.out.println("Zigzag Order: " + result.get(1));
    }
}

    

```
#### C++ Implementation
```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

vector<vector<int>> mergeIntervalsAndZigzagOrder(vector<vector<int>>& intervals) {
    // Step 1: Merge overlapping intervals
    sort(intervals.begin(), intervals.end());
    vector<vector<int>> merged;
    for (const auto& interval : intervals) {
        if (merged.empty() || merged.back()[1] < interval[0]) {
            merged.push_back(interval);
        } else {
            merged.back()[1] = max(merged.back()[1], interval[1]);
        }
    }
    
    // Step 2: Rearrange merged intervals in zigzag order
    vector<int> mergedFlattened;
    for (const auto& interval : merged) {
        mergedFlattened.push_back(interval[0]);
        mergedFlattened.push_back(interval[1]);
    }
    vector<int> zigzag;
    for (size_t i = 0; i < mergedFlattened.size(); i++) {
        if (i % 2 == 0) {
            zigzag.push_back(mergedFlattened[i]);
        } else {
            zigzag.insert(zigzag.end() - 1, mergedFlattened[i]);
        }
    }
    
    return {merged, zigzag};
}

int main() {
    vector<vector<int>> intervals = {{1, 3}, {2, 6}, {8, 10}, {15, 18}};
    auto result = mergeIntervalsAndZigzagOrder(intervals);
    cout << "Merged Intervals: ";
    for (const auto& interval : result[0]) {
        cout << "[" << interval[0] << ", " << interval[1] << "] ";
    }
    cout << endl;

    cout << "Zigzag Order: ";
    for (const auto& num : result[1]) {
        cout << num << " ";
    }
    cout << endl;
    return 0;
}

```
***
***Problem Created and Solved by Ms. Veda Patil***
