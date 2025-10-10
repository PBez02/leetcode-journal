Name: Peter Bezgoubov
Date: 10/10/2025
Problem: Reverse Linked List

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
   ListNode* reverseList(ListNode* head) {
       ListNode* prev = nullptr;
       ListNode* current = head;


       while (current != nullptr) {
           ListNode* temp = current->next;
           current->next = prev;
           prev = current;
           current = temp;
       }
       head = prev;
       return head;
   }
};


Writeup: Set 2 pointers, one pointing to current, the other pointing to “prev” element (initially null). It is much easier to explain this in a diagram line by line.

First line, List Node* temp = current->next;
nullptr  [node1(current)]---->[node2(temp)]---->[node3]---->[node4]---->nullptr

current->next = prev;
nullptr(prev)<----[node1(current)]  [node2(temp)]---->[node3]---->[node4]---->nullptr

prev = current;
nullptr<----[node1(current/prev)]   [node2(temp)]---->[node3]---->[node4]---->nullptr

current = temp
nullptr<----[node1(prev)]   [node2(current/temp)]---->[node3]---->[node4]---->nullptr

Repeat until
nullptr<----[node1]<----[node2]<----[node3]<----[node4(prev)]<---- nullptr(current/temp)

Then just set head = prev and done.

Complexity: Time = O(n), Space = O(1)
