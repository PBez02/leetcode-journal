Name: Peter Bezgoubov
Date: 12/10/2025
Problem: Linked List Cycle

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
    bool hasCycle(ListNode* head) {
        ListNode* fast = head;
        ListNode* slow = head;

        while (fast && fast->next) {
            slow = slow->next;
            fast = fast->next->next;
            if (slow == fast) {
                return true;
            }
        }
        return false;
    }
};

Writeup: This short solution makes use of Floyd's cycle-finding algorithm which makes use of a slow pointer and a fast pointer. One pointer increments by 1 and the other increments by 2 through the linked list. There is a mathematical proof as to why if there is a cycle eventually these pointers will meet but I won't write that here, just know that it works. If there is no cycle, the fast pointer will become nullptr and break out of the loop and return false.

Complexity: Time = O(n), Space = O(1)
