# Symmetric Tree
<https://leetcode.com/problems/symmetric-tree/description/>

## Description
Given the root of a binary tree, check whether it is a mirror of itself (i.e., symmetric around its center).

**Example 1:**

>**Input:** root = [1,2,2,3,4,4,3]  
**Output:** true

## Solution
A recursive function can probably solve this. We have to first take care of the base case, so if the left and right of our root are both null we can return true, as a 1 node tree is symmetrical. Next we make a recursive function isSame, and we pass it arguments for the left and right nodes. If either node is null, we have to make sure the other one is, so we return whether those nodes equal each other. We then recursively call our function in our return statement, where we first check the values of the left and right node, and then call isSame with the left nodes right child and the right nodes left child and call isSame again with the left nodes left child and the right nodes right child. We compare all three of these booleans and return them.

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
    bool isSymmetric(TreeNode* root) {
        // base case
        if(root->left == nullptr && root->right == nullptr) return true;
        // recursive call
        return isSame(root->left, root->right);
        
    }
    bool isSame(TreeNode* leftNode, TreeNode* rightNode) {
        if(leftNode == nullptr || rightNode == nullptr) return leftNode == rightNode;
        return leftNode->val == rightNode->val && isSame(leftNode->right, rightNode->left) && isSame(leftNode->left, rightNode->right);
    }
};