Name: Peter Bezgoubov
Date: 3/11/2025
Problem: Copy Linked List with Random Pointer

/*
// Definition for a Node.
class Node {
public:
    int val;
    Node* next;
    Node* random;
   
    Node(int _val) {
        val = _val;
        next = NULL;
        random = NULL;
    }
};
*/


class Solution {
public:
    Node* copyRandomList(Node* head) {
        unordered_map<Node*, Node*> hashmap;
        hashmap[NULL] = NULL;


        Node* current = head;
        while (current) {
            Node* copy = new Node(current->val);
            hashmap[current] = copy;
            current = current->next;
        }


        current = head;
        while (current) {
            Node* copy = hashmap[current];
            copy->next = hashmap[current->next];
            copy->random = hashmap[current->random];
            current = current->next;
        }


        return hashmap[head];
    }
};

Writeup: We basically create a hash map with a Node-Node pair. We store each node in the hash map and its corresponding copy node as its value. We then loop through the hashmap again, this time to link all the copy nodes together, setting the next and random values.

Complexity: Time = O(n), Space = O(n) (Two-pass)
