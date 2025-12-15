Name: Peter Bezgoubov
Date: 16/10/2025
Problem: Binary Tree Level Order Traversal

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
   vector<vector<int>> levelOrder(TreeNode* root) {
       vector<vector<int>> ans;
       queue<TreeNode*> q1;
       if (root) q1.push(root);
      
       while (!q1.empty()) {
           int sz = q1.size();
           vector<int> temp;
           for (int i = 0; i < sz; i++) {
               TreeNode* curr = q1.front();
               q1.pop();
               temp.push_back(curr->val);
               if (curr->left) q1.push(curr->left);
               if (curr->right) q1.push(curr->right);
           }
           ans.push_back(temp);
       }
       return ans;
   }
};

Writeup: Just BFS.

Complexity: Time = O(n), Space = O(n)
