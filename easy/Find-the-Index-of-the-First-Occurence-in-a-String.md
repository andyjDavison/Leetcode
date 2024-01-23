# Find the Index of the First Occurence in a String
<https://leetcode.com/problems/find-the-index-of-the-first-occurrence-in-a-string/description/>

## Description
Given two strings needle and haystack, return the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.

**Example 1:**

>**Input:** haystack = "sadbutsad", needle = "sad"  
**Output:** 0  
**Explanation:** "sad" occurs at index 0 and 6.
The first occurrence is at index 0, so we return 0.


## Solution
Simply check if the length of the haystack is longer than the needle, and if not return -1. Else we just use the std::find function on our needle and haystack

## Complexity
Time Complexity: O(1)

## Code
#### C++
    class Solution {
    public:
        int strStr(string haystack, string needle) {
            if(haystack.length() < needle.length()) return -1;
            return haystack.find(needle);
        }
    };