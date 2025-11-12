Name: Peter Bezgoubov
Date: 12/11/2025
Problem: Invert Binary Tree

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
   TreeNode* invertTree(TreeNode* root) {
       if (root == nullptr) {
           return nullptr;
       }
       TreeNode* temp = root->left;
       root->left = root->right;
       root->right = temp;
       invertTree(root->left);
       invertTree(root->right);
       return root;
   }
};

Writeup: This problem is quite straightforward. It uses a recursive solution where we take a node, look at its 2 children, then make a swap. We then go into the children and recursively perform invert on the children as well. The recursion stops once it reaches a nullptr.

Complexity: Time = O(n), Space = O(n)
