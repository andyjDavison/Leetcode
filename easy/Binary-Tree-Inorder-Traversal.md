# Binary Tree Inorder Traversal
<https://leetcode.com/problems/binary-tree-inorder-traversal/description/>

## Description
Given the root of a binary tree, return the inorder traversal of its nodes' values.

**Example 1:**

>**Input:** root = [1,null,2,3]  
**Output:** [1,3,2]

## Solution
A simple recursive function will work here. We create function inOrderList, that takes a TreeNode node, and a list as arguments. If the Node is null, there is nothing to add, so return what was in the list already. Otherwise, we just recursively perform an inorder traversal (parent->left->right), and after the search performed on the left child, we add that node's value to the list. return the list at the end of traversal. 

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
    vector<int> inorderTraversal(TreeNode* root) {
        vector<int> list;
        return inOrderList(root, list);
    }
    vector<int> inOrderList(TreeNode* node, vector<int>& list) {
        if(node == nullptr) return list;

        inOrderList(node->left, list);
        list.push_back(node->val);
        inOrderList(node->right,list);
        return list;
    }
};
```