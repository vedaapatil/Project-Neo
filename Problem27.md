# Shortest Prime-Sum Cube Permutations


### Problem Statement

Find the smallest prime number whose cube has exactly four permutations that are also the cubes of primes.

### Tags

```Prime numbers```  ```Number theory```  ```Combinatorics``` 





### Explanation

Find the smallest prime number whose cube has exactly four permutations that are also cubes of
primes.
### Steps:
1. Generate prime numbers.
2. Calculate their cubes.
3. Sort the digits of each cube.
4. Store cubes in a dictionary by sorted digits.
5. Find the entry with exactly four permutations.


### Solution
```
11
```
### Pseudocode

```text
initialize list of prime numbers up to a certain limit
create a dictionary to store cubes and their permutations

for each prime number p in the list:
    cube = p^3
    sort the digits of cube
    store the sorted digits in the dictionary with the original cube as a value

for each entry in the dictionary:
    if the entry has exactly four permutations which are cubes:
        return the smallest original prime corresponding to the cube

```

### Implementation

#### Python Implementation
```python

  from sympy import primerange

def is_prime(n):
    if n <= 1:
        return False
    if n <= 3:
        return True
    if n % 2 == 0 or n % 3 == 0:
        return False
    i = 5
    while i * i <= n:
        if n % i == 0 or n % (i + 2) == 0:
            return False
        i += 6
    return True

def prime_cubes_with_permutations(limit):
    primes = list(primerange(1, limit))
    cubes = {}
    
    for p in primes:
        cube = p ** 3
        sorted_cube = ''.join(sorted(str(cube)))
        if sorted_cube in cubes:
            cubes[sorted_cube].append(cube)
        else:
            cubes[sorted_cube] = [cube]
    
    for key, value in cubes.items():
        if len(value) == 4:
            return min(value) ** (1/3)
    
    return None

print(int(prime_cubes_with_permutations(10000)))
  

   
```
#### Java Implementation
```java
import java.util.*;

public class PrimeCubePermutations {

    public static boolean isPrime(int n) {
        if (n <= 1) return false;
        if (n <= 3) return true;
        if (n % 2 == 0 || n % 3 == 0) return false;
        for (int i = 5; i * i <= n; i += 6) {
            if (n % i == 0 || n % (i + 2) == 0) return false;
        }
        return true;
    }

    public static List<Integer> generatePrimes(int limit) {
        List<Integer> primes = new ArrayList<>();
        for (int num = 2; num < limit; num++) {
            if (isPrime(num)) {
                primes.add(num);
            }
        }
        return primes;
    }

    public static int findSmallestPrimeCube() {
        List<Integer> primes = generatePrimes(10000);
        Map<String, List<Integer>> cubes = new HashMap<>();
        
        for (int p : primes) {
            int cube = p * p * p;
            char[] sortedCube = String.valueOf(cube).toCharArray();
            Arrays.sort(sortedCube);
            String key = new String(sortedCube);
            cubes.computeIfAbsent(key, k -> new ArrayList<>()).add(cube);
        }
        
        for (Map.Entry<String, List<Integer>> entry : cubes.entrySet()) {
            if (entry.getValue().size() == 4) {
                return (int) Math.cbrt(Collections.min(entry.getValue()));
            }
        }
        
        return -1;
    }

    public static void main(String[] args) {
        System.out.println(findSmallestPrimeCube());
    }
}

```
#### C++ Implementation
```cpp
#include <iostream>
#include <vector>
#include <map>
#include <algorithm>
#include <cmath>

bool isPrime(int n) {
    if (n <= 1) return false;
    if (n <= 3) return true;
    if (n % 2 == 0 || n % 3 == 0) return false;
    for (int i = 5; i * i <= n; i += 6) {
        if (n % i == 0 || n % (i + 2) == 0) return false;
    }
    return true;
}

std::vector<int> generatePrimes(int limit) {
    std::vector<int> primes;
    for (int num = 2; num < limit; num++) {
        if (isPrime(num)) {
            primes.push_back(num);
        }
    }
    return primes;
}

int findSmallestPrimeCube() {
    std::vector<int> primes = generatePrimes(10000);
    std::map<std::string, std::vector<int>> cubes;
    
    for (int p : primes) {
        int cube = p * p * p;
        std::string sortedCube = std::to_string(cube);
        std::sort(sortedCube.begin(), sortedCube.end());
        cubes[sortedCube].push_back(cube);
    }
    
    for (const auto& entry : cubes) {
        if (entry.second.size() == 4) {
            return static_cast<int>(std::cbrt(*std::min_element(entry.second.begin(), entry.second.end())));
        }
    }
    
    return -1;
}

int main() {
    std::cout << findSmallestPrimeCube() << std::endl;
    return 0;
}

```
***
***Problem Created and Solved by Ms. Veda Patil***
