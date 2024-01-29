# Balanced Binary Tree
<https://leetcode.com/problems/balanced-binary-tree/>

## Description
Given a binary tree, determine if it is
height-balanced.

**Example 1:**

>**Input:** root = [3,9,20,null,null,15,7]  
**Output:** true

## Solution
Solve this with a fairly complex recursive function. We first create a function to count the amount of subtrees of a node. In this function we must first check the base case, if the node is null, we return 0. Otherwise we recursively call this function in our return statement, where we return the max length of a subtree in the node. Note we have to add 1 to this return statement, otherwise it will always return 0. Now in our main function we must once again check the base case, and here if the root node is null, we return true as it is balanced. Our return statement here is where it gets complicated, as we must return a boolean expression where the first term is the difference between the right and left subtree's heights and if this difference is less than or equal to 1, we get true. The next term we recursively call our main function with the left subtree, and then our last term is a recursive call with the right subtree. If all three are true we have a balanced binary tree.

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
    bool isBalanced(TreeNode* root) {
        if(root == nullptr) return true;
        return abs(countSubtrees(root->left)-countSubtrees(root->right)) <= 1 && isBalanced(root->left) && isBalanced(root->right);
    }
    int countSubtrees(TreeNode* root) {
        if(root == nullptr) return 0;
        return max(countSubtrees(root->left), countSubtrees(root->right))+1;
    }
};