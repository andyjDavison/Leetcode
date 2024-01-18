# Longest Common Prefix
<https://leetcode.com/problems/longest-common-prefix/description/>

## Description
Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string "".

**Example 1:**

>**Input:** strs = ["flower","flow","flight"]  
**Output:** "fl"

## Solution
First deal with edge cases, i.e. if the list of strings is empty return "". I set the prefix to the string at the first index of the list. I then loop through the remaining strings in the list. We loop through each string using the find() function, making sure we haven't found the prefix in this string so far. We continually cut the string's last character off, and continue checking until, that prefix shows up in the string. If the prefix doesn't exist in that string return "", as there is no common prefix. Do this for each string in the list until the we reach the end.

## Complexity
Time Complexity: O(n^2)

## Code
#### C++
    class Solution {
    public:
        string longestCommonPrefix(vector<string>& strs) {
            if(strs.size() == 0) return "";
            string prefix = strs[0];
            for(int i=1;i<strs.size();i++) {
                while(strs[i].find(prefix) != 0) {
                    prefix = prefix.substr(0,prefix.length()-1);
                    if(prefix.length() == 0) return "";
                }
            }
            return prefix;
        }
    };