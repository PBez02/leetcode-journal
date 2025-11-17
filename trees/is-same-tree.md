Name: Peter Bezgoubov
Date: 16/11/2025
Problem: Is Same Tree

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
};


Writeup: This solution is pretty straightforward; we just run DFS at every node and check if they are equal. If it isn’t, we return false. The only trick party is figuring out that if nodes are equal, you place the next recursive step inside that if statement.

Complexity: Time = O(n), Space = O(n)
