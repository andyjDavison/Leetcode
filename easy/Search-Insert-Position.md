# Search Insert Position
<https://leetcode.com/problems/search-insert-position/description/>

## Description
Given a sorted array of distinct integers and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

You must write an algorithm with O(log n) runtime complexity.

**Example 1:**

>**Input:** nums = [1,3,5,6], target = 5  
**Output:** 2

## Solution
It's kind of given away in the description since we need a runtime complexity of O(log n), that we should use a recursive search here. I created an overloaded function, that takes an array nums, a left index, a right index, and a target. In this function, we must make sure every call that the right index is greater than the left, which otherwise signals we have found our target position. If we haven't found our position yet, we need to calculate the middle index of our list, and then check either side of that against the target. Then we continue to recursively call this function until the end.

## Complexity
Time Complexity: O(log(n))

## Code
#### C++
```c++
class Solution {
public:
    int searchInsert(vector<int>& nums, int target) {
        return searchInsert(nums, 0, nums.size()-1, target);
    }
    int searchInsert(vector<int>& nums, int left, int right, int target) {
        if(right > left) {
            int mid = left+(right-left)/2;
            if(nums[mid] == target) 
                return mid;
            else if(nums[mid] > target) 
                return searchInsert(nums, left, mid-1, target);
            else
                return searchInsert(nums, mid+1, right, target);
        }
        return nums[left] < target ? left + 1 : left;
    }
};