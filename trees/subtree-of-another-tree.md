Name: Peter Bezgoubov
Date: 17/11/2025
Problem: Subtree of Another Tree

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


   bool isSameTree(TreeNode* p, TreeNode* q) {
       if (p == nullptr && q == nullptr) {
           return true;
       }
       if ((p && q) && (p->val == q->val)) {
           return isSameTree(p->left, q->left) && isSameTree(p->right, q->right);
       }
       return false;
   }


   bool isSubtree(TreeNode* root, TreeNode* subRoot) {
       if (!subRoot) return true;
       if (!root) return false;
       if (isSameTree(root, subRoot)) return true;
       return (isSubtree(root->left, subRoot) ||
           isSubtree(root->right, subRoot));
   }
};


Writeup: This problem is an extension of the previous problem where we find the same tree. We basically just recursively check at every node in the main tree if the other tree is the same. If it is we know that the 2nd tree is a subtree, if it isn’t we continue the search until we find a match. If there is no match we simply return false.

Complexity: Time = O(m * n), Space = O(m + n)
