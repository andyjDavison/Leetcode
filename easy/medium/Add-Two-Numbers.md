# Add Two Numbers
<https://leetcode.com/problems/add-two-numbers/>

## Description
You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

**Example 1:**  

>**Input:** l1 = [2,4,3], l2 = [5,6,4]  
**Output:** [7,0,8]  
**Explanation:** 342 + 465 = 807.

## Solution
Very straightforward solution, just need to move through both lists, keep track of carried values, and make sure we haven't hit the end of either list. Beginning we create a list with the first node being 0, and a carry value initialized at 0. So using a while loop that keeps running while either list is not null, or carry is 1 we do something. What we do is check if each list is null, and if it isn't we add the value at the current node to our sum. Then once we have checked both lists we add our sum to the carry. If we have a carry, we need to calculate it taking the modulous of the sum and 10. Then we just iterate to the next node and do this until all of the conditions of the while loop are false.

## Complexity
Time Complexity: O(max(N, M)) where N is the length of l1 and M is the length of l2

## Code
#### C++
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
        ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
            ListNode *ans = new ListNode(0);
            ListNode *curr = ans;
            int carry = 0;
            while(l1 != NULL || l2 != NULL || carry == 1) {
                int sum = 0;
                if(l1 != NULL) { // add l1 to the sum and move to next node
                    sum += l1->val;
                    l1 = l1->next;
                }
                if(l2 != NULL) { // add l2 to the sum and move to next node
                    sum += l2->val;
                    l2 = l2->next;
                }
                sum += carry; // if we have a carry we have to add it
                carry = sum/10; // if we get carry, divide by 10 to get it
                curr->next = new ListNode(sum % 10); // the value to add to our list will be the sum % 10
                curr = curr->next; // move to the next node
            }
            return ans->next;
        }
    };