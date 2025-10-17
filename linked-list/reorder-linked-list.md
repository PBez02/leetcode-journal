Name: Peter Bezgoubov
Date: 17/10/2025
Problem: Reorder Linked List


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
    void reorderList(ListNode* head) {
        ListNode* slow = head;
        ListNode* fast = head->next;
        while (fast != nullptr && fast->next != nullptr) {
            slow = slow->next;
            fast = fast->next->next;
        }


        ListNode* second = slow->next;
        slow->next = nullptr;
        ListNode* prev = nullptr;
        while (second != nullptr) {
            ListNode* temp = second->next;
            second->next = prev;
            prev = second;
            second = temp;
        }


        ListNode* first = head;
        second = prev;
        while (second != nullptr) {
            ListNode* temp1 = first->next;
            ListNode* temp2 = second->next;
            first->next = second;
            second->next = temp1;
            first = temp1;
            second = temp2;
        }
       
    }
};


Writeup: This solution is a bit tricky and has 3 parts so I will explain it as such:

Part 1: First initialise a slow pointer and fast pointer. The slow pointer will finish at the end of the first half of the list and the fast pointer will finish at the end of the list.

[num1] —-> [num2] —-> [num3/slow] —-> [num4] —-> [num5] —-> [num6/fast]

Part 2: We use the slow pointer position to now begin a reversal of the second half of the list. Once we finish this. Our setup should now look something like this:

[num1] —-> [num2] —-> [num3] —-> nullptr
[num6/second] —-> [num5] —-> [num4] —-> nullptr

Part 3: Now we just need to simply start from the beginning and merge the 2 lists together. We do this by first initializing our 2 temp variables which are first->next and second->next. After which we set first->next to second and second->next to temp1. Then we simply set first and second back to our temporary variables that we created until we have finished merging the list.

Complexity: Time = O(n), Space = O(1)

