Name: Peter Bezgoubov
Date: 16/10/2025
Problem: Lowest Common Ancestor of a Binary Search Tree

/**
* Definition for a binary tree node.
* struct TreeNode {
*     int val;
*     TreeNode *left;
*     TreeNode *right;
*     TreeNode() : val(0), left(nullptr), right(nullptr) {}
*     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
*     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
* };
*/


class Solution {
public:
   TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) {
       TreeNode* curr = root;


       while (curr) {
           if (p->val < curr->val && q->val < curr->val) {
               curr = curr->left;
           }
           else if (p->val > curr->val && q->val > curr->val) {
               curr = curr->right;
           }
           else {
               return curr;
           }
       }
       return nullptr;
   }
};



Writeup: Make use of the fact it’s a binary search tree by check if both values are less than or greater than the current node. If both are less, go left. If both are more, go right. If neither then we know the current node is the lowest ancestor.

Complexity: Time = O(h), Space = O(1)
