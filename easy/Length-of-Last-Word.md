# Length of Last Word
<https://leetcode.com/problems/length-of-last-word/>

## Description
Given a string s consisting of words and spaces, return the length of the last word in the string.

A word is a maximal
substring
consisting of non-space characters only.

**Example 1:**

>**Input:** s = "Hello World"  
**Output:** 5  
**Explanation:** The last word is "World" with length 5.

## Solution
Initial thinking is to start from end of the string and find the length of the first set of characters after a space. We need a count, which will keep track of the length of our word, and a flag, to make sure we get rid of spaces that are at the end of the string. We loop from the end of the string to 0, and at every character we check if it is a space and the flag is true, or if it is not a space. If the current character is a space and the flag is true, this means we have seen a letter already, and that we should break out of the loop. Otherwise we have encountered a letter, and we need to add one to the count. We go until the end of the string, or until we encounter another space.

## Complexity
Time Complexity: O(n)

## Code
#### C++
```c++
class Solution {
public:
    int lengthOfLastWord(string s) {
        int count = 0, flag = 0;
        for(int i=s.length()-1;i>=0;i--) {
            // first space that has had a letter in front of it already
            if(s[i] == ' ' && flag) break;
            // encounter the first char that isn't a space 
            if(s[i] != ' ') { 
                flag = 1;
                count++;
            }
        }
        return count;
    }
};