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
        ListNode* dummy = new ListNode();
        ListNode* curr = dummy;
        int carry = 0;
        while (l1 || l2 || carry != 0) {
            int x = 0;
            int y = 0;
            if (l1 != nullptr) {
                x = l1->val;
            }
            if (l2 != nullptr) {
                y = l2->val;
            }
            int curr_sum = x + y + carry;
            curr->next = new ListNode(curr_sum % 10);
            carry = curr_sum / 10;
            curr = curr->next;
            if (l1) {
                l1 = l1->next;
            }
            if (l2) {
                l2 = l2->next;
            }
        }
        ListNode* result = dummy->next;
        delete dummy;
        return result;
    }
};


Writeup: We first initialise a dummy ListNode to store our sum inside. We then create a variable carry to store the carry of our addition operations. We loop and check if any of these 3 conditions are valid. (1) if list 1 has a value, (2) if list 2 has a value, (3) is there a value currently stored in the carry? If any of these 3 are true, we must continue with the loop.

We just check if l1 or l2 is null, if it is, we just keep the value as 0. We add them up with our carry value, then continue. We take the sum, modulus it by 10 and create a new node and attach it to our list. We then compute if there is any carry value that needs to be brought forward to the next loop.

Lastly, we just create a ListNode result and store the list inside and delete our dummy list.

Complexity: Time = O(max(m, n)), Space = O(1)
