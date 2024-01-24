# Maximum Depth of Binary Tree
<https://leetcode.com/problems/maximum-depth-of-binary-tree/description/>

## Description
Given the root of a binary tree, return its maximum depth.

A binary tree's maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.

**Example 1:**

>**Input:** root = [3,9,20,null,null,15,7]  
**Output:** 3

## Solution
Simple recursive solution, where we recursively check down each subtree. Start with the base case, where if the root is null, return 0. Then we need to check the left subtree recursively, and the right subtree as well. At the end of the function we need to get the maximum between the left and right, but we have to add 1 to it, as to start the function we return 0, so adding one will actually get us a value. We then return the maximum of these for the answer.

## Complexity
Time Complexity: O(log n)

## Code
#### C++
```c++
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    int maxDepth(TreeNode* root) {
        if(root == nullptr) return 0;
        // recursively check right subtree
        //int left = maxDepth(root->left);
        // recursively check left subtree
        //int right = maxDepth(root->right);
        // get the max between left and right
        return max(maxDepth(root->left), maxDepth(root->right)) + 1;
    }
};