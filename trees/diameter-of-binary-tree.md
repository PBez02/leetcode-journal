Name: Peter Bezgoubov
Date: 15/11/2025
Problem: Diameter of Binary Tree

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


   int max_height(TreeNode* node, int& total) {
       if (node == nullptr) {
           return -1;
       }
       int left = max_height(node->left, total) + 1;
       int right = max_height(node->right, total) + 1;
       total = std::max(total, left + right);
       return max(left,right);
   }


   int diameterOfBinaryTree(TreeNode* root) {
       if (root == nullptr) {
           return 0;
       }
       int total = 0;
       max_height(root, total);
       return total;
   }
};


Writeup: To do this problem, you need to first realise it’s a recursion problem. Then you can settle your base case and so on. I use a helper function to run a sort of DFS algorithm on the tree. This problem requires us to find the length of the longest path between any 2 nodes in the tree. 

We first need to instantiate a global variable to count our total diameter, you will see why later. We basically want to check the height of our left subtree and our right subtree and add them together and see if it is longer than our current measured diameter, if it is, we update the global variable total. We then return the height of the subtree to the parent function.

Complexity: Time = O(n), Space = O(n)
