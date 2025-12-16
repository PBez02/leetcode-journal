Name: Peter Bezgoubov
Date: 16/10/2025
Problem: Binary Tree Right Side View

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
   vector<int> rightSideView(TreeNode* root) {
       vector<int> ans;
       queue<TreeNode*> q;
       if (root) q.push(root);


       while (!q.empty()) {
           TreeNode* temp = q.front();
           int size = q.size();
           for (int i = 0; i < size; i++) {
               TreeNode* curr = q.front();
               q.pop();
               temp = curr;
               if (curr->left) q.push(curr->left);
               if (curr->right) q.push(curr->right);
           }
           ans.push_back(temp->val);
       }
       return ans;
   }
};



Writeup: Use BFS to traverse each level and just add the last node on each level to the vector.

Complexity: Time = O(n), Space = O(n)
