Name: Peter Bezgoubov
Date: 11/10/2025
Problem: Merge Two Sorted Lists

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
        ListNode final_list(0);
        ListNode* node = &final_list;


        while (list1 && list2) {
            if (list1->val < list2->val) {
                node->next = list1;
                list1 = list1->next;
            }
            else {
                node->next = list2;
                list2 = list2->next;
            }
            node = node->next;
        }


        if (list1) {
            node->next = list1;
        }
        else {
            node->next = list2;
        }
        return final_list.next;
    }
};


Writeup: We first initialize a new linked list node to start the construction of a new sorted list. We then loop through both lists and compare the current node to see which one is bigger or smaller. The smaller value gets stored into the new list. If one list goes null, e.g., list1, we exit the loop and simply set the rest of our new list to be the rest of list2.

Complexity: Time = O(n + m), Space = O(1)
