# Common in Merged Lists

### Problem Statement

Find common elements between two lists after merging them into one sorted list.
### Tags

```List```  ```Merge```  ``` Common```  ```Elements```   ```Sorted``` 


### Explanation

This combines merging sorted lists and finding common elements by first merging the lists and then identifying the common elements.
### Solution
```
[3, 5]
```
### Pseudocode

```text
function commonInMergedLists(list1, list2):
    merged_list = merge(list1, list2)
    common_elements = []
    
    for element in merged_list:
        if element in list1 and element in list2:
            if element not in common_elements:
                common_elements.append(element)
    
    return common_elements

function merge(list1, list2):
    result = []
    i = 0
    j = 0
    
    while i < length of list1 and j < length of list2:
        if list1[i] < list2[j]:
            result.append(list1[i])
            i += 1
        else:
            result.append(list2[j])
            j += 1
    
    while i < length of list1:
        result.append(list1[i])
        i += 1
    
    while j < length of list2:
        result.append(list2[j])
        j += 1
    
    return result

```

### Implementation

#### Python Implementation
```python
def merge_sorted_lists(list1, list2):
    result = []
    i, j = 0, 0
    while i < len(list1) and j < len(list2):
        if list1[i] < list2[j]:
            result.append(list1[i])
            i += 1
        else:
            result.append(list2[j])
            j += 1
    result.extend(list1[i:])
    result.extend(list2[j:])
    return result

def common_in_merged_lists(list1, list2):
    merged_list = merge_sorted_lists(list1, list2)
    common_elements = []
    for element in merged_list:
        if element in list1 and element in list2 and element not in common_elements:
            common_elements.append(element)
    return common_elements

# Sample Input
list1 = [1, 3, 5, 7]
list2 = [2, 3, 5, 8]
print(common_in_merged_lists(list1, list2))  # Output: [3, 5]

```
#### Java Implementation
```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

public class CommonInMergedSortedLists {
    public static List<Integer> mergeSortedLists(int[] list1, int[] list2) {
        List<Integer> result = new ArrayList<>();
        int i = 0, j = 0;
        while (i < list1.length && j < list2.length) {
            if (list1[i] < list2[j]) {
                result.add(list1[i++]);
            } else {
                result.add(list2[j++]);
            }
        }
        while (i < list1.length) result.add(list1[i++]);
        while (j < list2.length) result.add(list2[j++]);
        return result;
    }

    public static List<Integer> commonInMergedLists(int[] list1, int[] list2) {
        List<Integer> mergedList = mergeSortedLists(list1, list2);
        List<Integer> commonElements = new ArrayList<>();
        for (int num : mergedList) {
            if (Arrays.binarySearch(list1, num) >= 0 && Arrays.binarySearch(list2, num) >= 0 && !commonElements.contains(num)) {
                commonElements.add(num);
            }
        }
        return commonElements;
    }

    public static void main(String[] args) {
        int[] list1 = {1, 3, 5, 7};
        int[] list2 = {2, 3, 5, 8};
        System.out.println(commonInMergedLists(list1, list2));  // Output: [3, 5]
    }
}

    

```
#### C++ Implementation
```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

vector<int> mergeSortedLists(const vector<int>& list1, const vector<int>& list2) {
    vector<int> result;
    int i = 0, j = 0;
    while (i < list1.size() && j < list2.size()) {
        if (list1[i] < list2[j]) {
            result.push_back(list1[i++]);
        } else {
            result.push_back(list2[j++]);
        }
    }
    while (i < list1.size()) result.push_back(list1[i++]);
    while (j < list2.size()) result.push_back(list2[j++]);
    return result;
}

vector<int> commonInMergedLists(const vector<int>& list1, const vector<int>& list2) {
    vector<int> mergedList = mergeSortedLists(list1, list2);
    vector<int> commonElements;
    for (int num : mergedList) {
        if (find(list1.begin(), list1.end(), num) != list1.end() &&
            find(list2.begin(), list2.end(), num) != list2.end() &&
            find(commonElements.begin(), commonElements.end(), num) == commonElements.end()) {
            commonElements.push_back(num);
        }
    }
    return commonElements;
}

int main() {
    vector<int> list1 = {1, 3, 5, 7};
    vector<int> list2 = {2, 3, 5, 8};
    vector<int> result = commonInMergedLists(list1, list2);
    for (int num : result) {
        cout << num << " ";
    }
    cout << endl;  // Output: 3 5
    return 0;
}

```
***
***Problem Created and Solved by Ms. Veda Patil***
