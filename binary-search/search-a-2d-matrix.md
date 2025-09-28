Name: Peter Bezgoubov
Date: 28/09/2025
Problem: Search a 2D Matrix

class Solution {
public:
    bool searchMatrix(vector<vector<int>>& matrix, int target) {
        if (matrix.size() == 0) {
            return false;
        }
        if (matrix[0].size() == 0) {
            return false;
        }
        int i = 0;
        int j = matrix.size()-1;
        while (i <= j) {
            int mid = (i + j) / 2;
            if (target > matrix[mid].back()) {
                i = mid + 1;
            }
            else if (target < matrix[mid][0]) {
                j = mid - 1;
            }
            else {
                int x = 0;
                int y = matrix[0].size() - 1;
                while (x <= y) {
                    int mid_in = (x + y) / 2;
                    if (target == matrix[mid][mid_in]) {
                        return true;
                    }
                    else if (target < matrix[mid][mid_in]) {
                        y = mid_in - 1;
                    }
                    else {
                        x = mid_in + 1;
                    }
                }
                return false;
            }
        }
        return false;
    }
};

Writeup: We first commit a binary search on the first column of the matrix to find out which array our target could be in. Once we found where our target may be. We conduct another binary search on that row to find our target. If the target is not found, we return false; if it is found, we return true.

Complexity: Time = O(log(m*n)), Space = O(1)
