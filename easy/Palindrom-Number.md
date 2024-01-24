# Palindrome Number
<https://leetcode.com/problems/palindrome-number/>

## Description
Given an integer x, return true if x is a
palindrome
, and false otherwise.

**Example 1:**

>**Input:** x = 121  
**Output:** true  
**Explanation:** 121 reads as 121 from left to right and from right to left.

## Solution
Essentially, we want to flip the entire number and compare it to the original to see if it is the same. First we get edge cases, i.e. if the number is negative it is not a palindrome. To flip the number we need to make use of the % and dividing by 10. We create a temp value to modify, which is the same as x, and then while that temp is not on its last digit we go about getting all the digits. We use temp%10 to get the last digit and then add it to our check value, and then divide our temp by 10 to get rid of that digit. We then check our values and return that boolean.

## Time Complexity
Time complexity: O(n)

## Code
#### C++:
```c++
class Solution {
public:
    bool isPalindrome(int x) {
        if(x<0) return false;
        long temp = x;
        long check = 0;
        while(temp>0) {
            check *= 10;
            check += temp%10;
            temp /= 10;
        }
        return check == x;
    }
};