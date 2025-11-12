Name: Peter Bezgoubov
Date: 12/11/2025
Problem: Maximum Depth of Binary Tree

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
   int maxDepth(TreeNode* root) {
       stack<pair<TreeNode*, int>> stack;
       stack.push({root, 1});
       int res = 0;


       while (!stack.empty()) {
           pair<TreeNode*, int> current = stack.top();
           stack.pop();
           TreeNode* node = current.first;
           int depth = current.second;
           if (node != nullptr) {
               res = max(res, depth);
               stack.push({node->left, depth + 1});
               stack.push({node->right, depth + 1});
           }
       }
       return res;
   }
};


Writeup: This solution uses DFS to help us find the max depth. The trick is when we push the nodes into the stack, we push it as a pair where the first value is the node and the second value is its current depth. Thus everytime we explore a node (pop it from the stack), we check if its current depth is greater than the biggest depth we have seen so far, if it is then we update our result variable.

You can also use BFS to solve this problem by just tracking how many levels you have explored so far which is probably easier to understand conceptually.

Complexity: Time = O(n), Space = O(n)
