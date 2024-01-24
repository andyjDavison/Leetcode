# Merge Two Sorted Lists
<https://leetcode.com/problems/merge-two-sorted-lists/description/>

## Description
You are given the heads of two sorted linked lists list1 and list2.

Merge the two lists into one sorted list. The list should be made by splicing together the nodes of the first two lists.

Return the head of the merged linked list.

Example 1:

Input: list1 = [1,2,4], list2 = [1,3,4]
Output: [1,1,2,3,4,4]

## Solution
Intial thinking is to use a recursive sort to merge the lists. Create function called merge, this will be our recursive function. We must check the base cases, so if either list is empty, return the other list, otherwise we compare values. If the value of list1 is less than list2, we want that value first, so we create a new list node that starts with the list1 value as head, and recursively calls the merge function, with the next value of list1 and all of list2. Do the opposite if the value of list2 is less than list1. Then when returning this function, it will give us the head of the new merged list.

## Complexity

## Code
#### C++
```c++
/**
* Definition for singly-linked list.
* struct ListNode {
*     int val;
*     ListNode *next;
*     ListNode() : val(0), next(nullptr) {}
*     ListNode(int x) : val(x), next(nullptr) {}
*     ListNode(int x, ListNode *next) : val(x), next(next) {}
* };
*/
class Solution {
public:
    ListNode* mergeTwoLists(ListNode* list1, ListNode* list2) {
        return merge(list1, list2);
    }
    ListNode* merge(ListNode* list1, ListNode* list2) {
        if(list1 == nullptr) return list2;
        else if(list2 == nullptr) return list1;
        else if(list1->val < list2->val) return new ListNode(list1->val, merge(list1->next, list2));
        else return new ListNode(list2->val, merge(list1, list2->next));
    }
};