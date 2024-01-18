# Two Sum
<https://leetcode.com/problems/two-sum/description/>

## Description
Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

**Example 1:**

>**Input:** nums = [2,7,11,15], target = 9  
**Output:** [0,1]  
**Explanation:** Because nums[0] + nums[1] == 9, we return [0, 1].

## Solution
The easiest solution I created, was a simple brute force solution. Simply loop through the array, loop from each index, to the end of the array, and add up each pair of ints. If they equal the target, return an array with those values.

## Complexity
Time Complexity: O(n^2)

## Code
    class Solution {
    public:
        vector<int> twoSum(vector<int>& nums, int target) {
            for(int i=0;i<nums.size()-1;i++) {
                for(int j=i+1;j<nums.size();j++) {
                    if(nums[i] + nums[j] == target) {
                        return {i, j};
                    }
                }
            }
            return {}; // no solution
        }
    };