# Sqrt(x)
<https://leetcode.com/problems/sqrtx/description/>

## Description
Given a non-negative integer x, return the square root of x rounded down to the nearest integer. The returned integer should be non-negative as well.

You must not use any built-in exponent function or operator.

* For example, do not use pow(x, 0.5) in c++ or x ** 0.5 in python.

**Example 1:**

>**Input:** x = 4  
**Output:** 2  
**Explanation:** The square root of 4 is 2, so we return 2.

## Solution
Simply loop through 0 to x and find the i that, when squared, is either less than or equal to x and i+1 is greate than. Simply return the i. If x is 0 or 1 however, simply return x. (need to optimize this with a binary search algorithm to cut time to O(log n))

## Complexity
Time Complexity: O(n)

## Code
#### C++
```c++
class Solution {
public:
    int mySqrt(int x) {
        for(long i=0;i<x;i++) {
            if((i*i) <= x && x < (i+1)*(i+1)) {
                return i;
            }
        }
        return x;
    }
};