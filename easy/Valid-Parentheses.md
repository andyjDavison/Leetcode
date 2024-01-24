# Valid Parentheses
<https://leetcode.com/problems/valid-parentheses/>

## Description
Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

1. Open brackets must be closed by the same type of brackets.  
2. Open brackets must be closed in the correct order.  
3. Every close bracket has a corresponding open bracket of the same type.

**Example 1:**

>**Input:** s = "()[]{}"  
**Output:** true

## Solution
Initial thinking is to use a stack to hold the opening brackets and then check the current characters against those. So we initialize an empty stack. We then traverse the input string by each character. So if the current character is an opening bracket we push it onto the stack. If the the current character is a closing bracket we check if the stack is empty, or if the closing bracket matches the top of the stack. If none, then they are not valid and we return false. Otherwise we just pop the top from the stack and continue through the string. If the stack is empty at the end of traversing the string, then the brackets were all valid.

## Complexity
Time Complexity: O(n)

## Code
#### C++
```c++
class Solution {
public:
    bool isValid(string s) {
        stack<char> opening;
        for(char c : s) {
            if(c == '(' || c == '{' || c == '[') {
                opening.push(c);
            } else {
                if(opening.empty() ||
                    (c == ')' && opening.top() != '(') ||
                    (c == '}' && opening.top() != '{') ||
                    (c == ']' && opening.top() != '[')) return false;
                opening.pop();
            }
        }
        return opening.empty();
    }
};