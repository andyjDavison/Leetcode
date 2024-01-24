# Same Tree
<https://leetcode.com/problems/same-tree/description/>

## Description
Given the roots of two binary trees p and q, write a function to check if they are the same or not.

Two binary trees are considered the same if they are structurally identical, and the nodes have the same value.

**Example 1:**

>**Input:** p = [1,2,3], q = [1,2,3]  
**Output:** true

## Solution
We can solve this with a simple recursive function, that simultaneously searches through both trees, and compares each tree's nodes. We need to check the base case, which is if either node is null. If either of them are null, we return if they are both null or not. We then return a long boolean experssion that's first part is comparing the values at both nodes, then recursively check the left-node, of both trees, and then the right nodes as well. This will return true if everything is true.

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
    bool isSameTree(TreeNode* p, TreeNode* q) {
        // base case
        if(p == nullptr || q == nullptr) return p == nullptr && q == nullptr;
        return p->val == q->val && isSameTree(p->left, q->left) && isSameTree(p->right, q->right);
    }
};