# Title
<https://leetcode.com/problems/minimum-depth-of-binary-tree/description/>

## Description
Given a binary tree, find its minimum depth.

The minimum depth is the number of nodes along the shortest path from the root node down to the nearest leaf node.

**Note:** A leaf is a node with no children.

**Example 1:**

**Input:** root = [3,9,20,null,null,15,7]
**Output:** 2

## Solution
Simple recursive funciton to find the minimum depth. We have to check the base case first, so if the root is null return 0. We create two integers, left and right, which recursively search each subtree. We then check if the left child is null, wich means the right subtree would be one longer, and if the right child is null, the left subtree would be 1 longer, so we would add one to those nodes. We then return the minimum of these two integers, left and right, and add 1 to it. Recursively returning to top it will return the shortest minimum depth.

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
    int minDepth(TreeNode* root) {
        if(root == nullptr) return 0;
        int left = minDepth(root->left);
        int right = minDepth(root->right);
        // the right is longer if the left is null
        if(root->left == nullptr) return right+1;
        // the left is longer if the right is null
        if(root->right == nullptr) return left+1;
        return min(left, right) + 1;
    }
};