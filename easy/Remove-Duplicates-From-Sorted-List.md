# Remove Duplicates From Sorted List
<https://leetcode.com/problems/remove-duplicates-from-sorted-list/description/>

## Description
Given the head of a sorted linked list, delete all duplicates such that each element appears only once. Return the linked list sorted as well.

**Example 1:**

>**Input:** head = [1,1,2]  
**Output:** [1,2]

## Solution
Deal with empty list first, so if the head is null, we simply just return it. We then simply loop through the list and every time we come across a node whose duplicate exists we remove it by pointing the head's next to the duplicate node's next, which removes the duplicate. Return the head once we reach the end of the list.

## Complexity
Time Complexity: O(n)

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
    ListNode* deleteDuplicates(ListNode* head) {
        if(head == nullptr) return head;
        ListNode* curr = head;
        while(head->next != nullptr) {
            if(head->val == head->next->val) head->next = head->next->next;
            else head = head->next;
        }
        return curr;
    }
};