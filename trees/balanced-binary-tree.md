Name: Peter Bezgoubov
Date: 15/11/2025
Problem: Balanced Binary Tree

Brute Force:
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


   int height(TreeNode* node) {
       if (node == nullptr) {
           return 0;
       }
       return 1 + std::max(height(node->left), height(node->right));
   }


   bool isBalanced(TreeNode* root) {
       if (root == nullptr) {
           return true;
       }
       int left_h = height(root->left);
       int right_h = height(root->right);
       int balance_factor = left_h - right_h;
       if (balance_factor > 1 || balance_factor < -1) {
           return false;
       }
       return isBalanced(root->left) && isBalanced(root->right);
   }
};


DFS:
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


   int dfs(TreeNode* node) {
       if (node == nullptr) {
           return 0;
       }
       int left = dfs(node->left);
       if (left == -1) {
           return -1;
       }
       int right = dfs(node->right);
       if (right == -1) {
           return -1;
       }
       if (std::abs(left-right) > 1) {
           return -1;
       }
       return 1 + std::max(left,right);
   }


   bool isBalanced(TreeNode* root) {
       return dfs(root) != -1;
   }
};



Writeup: For the brute force, we simply just recursively explore every node and compare the heights of the left and right subtrees. The reason why it is n^2 is because everytime you check if a node is balanced, you then called the height function to recursively check the heights of the left and right subtrees.

For the DFS approach, instead of outsourcing the checking of heights, you simply just include it inside the recursive steps. At everynode, you return the height and perform a check to see if it is balanced, if it is you return the height of the node, if not you return -1.

Complexity: 
Brute force -> Time = O(n^2), Space = O(n)
DFS -> Time = O(n), Space = O(h)
