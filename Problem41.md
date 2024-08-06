# Add and Remove in List

### Problem Statement

Write a function to add an element at the beginning of a list and then remove a specific element by its value.

### Tags

```List```  ```Add Element```  ``` Remove Element```  


### Explanation

This combines adding an element at the beginning and removing a specific element by its value in a list.
### Solution
```
[1, 2, 3, 7]
```
### Pseudocode

```text

  
function addAndRemoveElement(lst, elementToAdd, elementToRemove):
    lst.insert(0, elementToAdd)  # Add element at the beginning
    if elementToRemove in lst:
        lst.remove(elementToRemove)  # Remove element by value
    return lst

```

### Implementation

#### Python Implementation
```python

def add_and_remove_element(lst, element_to_add, element_to_remove):
    lst.insert(0, element_to_add)  # Add element at the beginning
    if element_to_remove in lst:
        lst.remove(element_to_remove)  # Remove element by value
    return lst

# Sample Input
lst = [2, 3, 5, 7]
element_to_add = 1
element_to_remove = 5
print(add_and_remove_element(lst, element_to_add, element_to_remove))  # Output: [1, 2, 3, 7]

```
#### Java Implementation
```java

import java.util.ArrayList;
import java.util.List;

public class AddAndRemoveListElements {
    public static List<Integer> addAndRemoveElement(List<Integer> lst, int elementToAdd, int elementToRemove) {
        lst.add(0, elementToAdd);  // Add element at the beginning
        lst.remove(Integer.valueOf(elementToRemove));  // Remove element by value
        return lst;
    }

    public static void main(String[] args) {
        List<Integer> lst = new ArrayList<>();
        lst.add(2);
        lst.add(3);
        lst.add(5);
        lst.add(7);
        int elementToAdd = 1;
        int elementToRemove = 5;
        System.out.println(addAndRemoveElement(lst, elementToAdd, elementToRemove));  // Output: [1, 2, 3, 7]
    }
}

```
#### C++ Implementation
```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

vector<int> addAndRemoveElement(vector<int>& lst, int elementToAdd, int elementToRemove) {
    lst.insert(lst.begin(), elementToAdd);  // Add element at the beginning
    auto it = find(lst.begin(), lst.end(), elementToRemove);
    if (it != lst.end()) {
        lst.erase(it);  // Remove element by value
    }
    return lst;
}

int main() {
    vector<int> lst = {2, 3, 5, 7};
    int elementToAdd = 1;
    int elementToRemove = 5;
    vector<int> result = addAndRemoveElement(lst, elementToAdd, elementToRemove);
    for (int num : result) {
        cout << num << " ";
    }
    cout << endl;  // Output: 1 2 3 7
    return 0;
}

```
***
***Problem Created and Solved by Ms. Veda Patil***
