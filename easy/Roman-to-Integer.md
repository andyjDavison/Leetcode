# Title
<https://leetcode.com/problems/roman-to-integer/description/>

## Description
Roman numerals are represented by seven different symbols: I, V, X, L, C, D and M.

>**Symbol**&emsp;&emsp;**Value**  
I&emsp;&emsp;&emsp;&emsp;&emsp;&nbsp;1  
V&emsp;&emsp;&emsp;&emsp;&emsp;5  
X&emsp;&emsp;&emsp;&emsp;&emsp;10  
L&emsp;&emsp;&emsp;&emsp;&emsp;&nbsp;50  
C&emsp;&emsp;&emsp;&emsp;&emsp;100  
D&emsp;&emsp;&emsp;&emsp;&emsp;500  
M&emsp;&emsp;&emsp;&emsp;&nbsp;&nbsp;&nbsp;1000

For example, **2** is written as **II** in Roman numeral, just two ones added together. **12** is written as **XII**, which is simply **X + II**. The number **27** is written as **XXVII**, which is **XX + V + II**.

Roman numerals are usually written largest to smallest from left to right. However, the numeral for four is not **IIII**. Instead, the number four is written as **IV**. Because the one is before the five we subtract it making four. The same principle applies to the number nine, which is written as IX. There are six instances where subtraction is used:

    I can be placed before V (5) and X (10) to make 4 and 9. 
    X can be placed before L (50) and C (100) to make 40 and 90. 
    C can be placed before D (500) and M (1000) to make 400 and 900.

Given a roman numeral, convert it to an integer.

**Example 2:**

>**Input:** s = "LVIII"  
**Output:** 58  
**Explanation:** L = 50, V= 5, III = 3.  


## Solution
First initial thinking is to put these given values into a map, and perform calculations that way. Only other thing to think about is the instances where subtraction is used. Simplest solution is to use conditionals, and check the next value after the I, X, and C. Add the corresponding values gathered from these conditionals to the total sum, and index correctly based on the number of checked positions. Return the sum.

## Complexity
Time Complexity: O(n) 

## Code
#### C++
    class Solution {
    public:
        int romanToInt(string s) {
            map<char, int> mp;
            mp['I'] = 1;
            mp['V'] = 5;
            mp['X'] = 10;
            mp['L'] = 50;
            mp['C'] = 100;
            mp['D'] = 500;
            mp['M'] = 1000;
            int sum = 0, i = 0;
            while(i<s.size()) {
                if(s[i] == 'I' && s[i+1] == 'V') {
                    sum += 4;
                    i += 2;
                } else if(s[i] == 'I' && s[i+1] == 'X') {
                    sum += 9;
                    i += 2;
                } else if(s[i] == 'X' && s[i+1] == 'L') {
                    sum += 40;
                    i += 2;
                } else if(s[i] == 'X' && s[i+1] == 'C') {
                    sum += 90;
                    i += 2;
                } else if(s[i] == 'C' && s[i+1] == 'D') {
                    sum += 400;
                    i += 2;
                } else if(s[i] == 'C' && s[i+1] == 'M') {
                    sum += 900;
                    i += 2;
                } else {
                    sum += mp[s[i]];
                    i++;
                }
            }
            return sum;
        }
    };