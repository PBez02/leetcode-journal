Name: Peter Bezgoubov
Date: 16/10/2025
Problem: Count Good Nodes in Binary Tree

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
   int goodNodes(TreeNode* root) {
       queue<pair<TreeNode*, int>> q1;
       if (root) q1.push({root, root->val});
       int c = 0;


       while (!q1.empty()) {
           auto [node, mv] = q1.front();
           q1.pop();


           if (node->val >= mv) c++;
           int nm = max(node->val, mv);
           if (node->left) q1.push({node->left, nm});
           if (node->right) q1.push({node->right, nm});
       }
       return c;
   }
};

Writeup: Use BFS and store each value in the queue as pair of 2 values. The first is the node, and second is the max value seen so far in its path. If the current node is greater than or equal to the max seen so far for it’s path, then we increment our counter.

Complexity: Time = O(n), Space = O(n)
