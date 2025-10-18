Name: Peter Bezgoubov
Date: 18/10/2025
Problem: Remove Nth Node From End Of List

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
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        if (head == nullptr) {
            return nullptr;
        }
        ListNode* current = head;
        int count = 0;
        while (current != nullptr) {
            current = current->next;
            count++;
        }
        count -= n;
        if (count == 0) {
            return head->next;;
        }
        current = head;
        ListNode* prev = nullptr;
        int ctr = 0;
        while (ctr < count && current != nullptr) {
            prev = current;
            current = current->next;
            ctr++;
        }
        prev->next = current->next;
        delete current;
        return head;
    }
};

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
   ListNode* removeNthFromEnd(ListNode* head, int n) {
       ListNode* dummy = new ListNode(0);
       dummy->next = head;
       ListNode* fast = dummy;
       ListNode* slow = dummy;
       for (int i = 0; i <= n; i++) {
           fast = fast->next;
       }
       while (fast != nullptr) {
           slow = slow->next;
           fast = fast->next;
       }
       ListNode* temp = slow->next;
       slow->next = slow->next->next;
       delete temp;
      
       head = dummy->next;
       delete dummy;
       return head;
   }
};

Writeup 1: My original solution was a 2 pass solution where we just figure out the total number of nodes in the list, then minus the count from the position of the node we want to remove. Then we traverse the list again keeping a prev pointer and a current pointer. Once we reach the node we want to remove, we make the prev pointer point to current->next then remove current. We then return the head of the list.

Writeup 2: This solution makes use of 2 pointers (slow and fast again). We first create a dummy node to make sure our starting point is before the beginning of the linked list. We progress the fast pointer until it is after the node we want to remove. Then we do another loop to shift our fast and slow pointers. In doing this we hit a point where our slow pointer is right before the node we want to remove. Then we simply just make the slow pointer point to slow->next->next (skipping over the node we want to remove) and remove slow->next. We then set our head to dummy->next, remove the dummy and return the head.

Complexity: Time = O(n) for both, Space = O(1) for both
