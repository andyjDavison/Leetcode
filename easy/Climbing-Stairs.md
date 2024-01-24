# Climbing Stairs
<https://leetcode.com/problems/climbing-stairs/description/>

## Description
You are climbing a staircase. It takes n steps to reach the top.

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

**Example 1:**

>**Input:** n = 2  
**Output:** 2  
**Explanation:** There are two ways to climb to the top.
>1. 1 step + 1 step  
>2. 2 steps

## Solution
Essentially a combination problem which can be solved using a modified version of C(n, r) = n!/r!(n-r)!. We set a variable ways which will be our count of the total number of ways to go up the stairs. We then use a nested loop, where i goes from 1 to n/2, to explore different stair sizes, and for each of those sizes, calculate the combinatorial. Store that in the sum variable and add that to the total number of ways after each step, then we can return that as our answer.

## Complexity
Time Complexity: O(n^2)

## Code
#### C++
```c++
class Solution {
public:
    int climbStairs(int n) {
        int ways = 1;
        for(int i=1;i<=n/2;i++) {
            double sum = 1; // stupid I left sum as 0
            for(int j=i;j<2*i;j++) {
                sum *= (double)(n-j)/(j-i+1);
            }
            ways += sum;
        }
        return ways;
    }
};