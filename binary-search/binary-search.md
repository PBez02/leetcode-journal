Name: Peter Bezgoubov
Date: 27/09/2025
Problem: Binary Search

class Solution {
public:
    int search(vector<int>& nums, int target) {
        int i = 0;
        int j = nums.size() - 1;
        while (i <= j) {
            int mid = (i + j) / 2;
            if (nums[mid] == target) {
                return mid;
            }
            else if (nums[mid] < target) {
                i = mid + 1;
            }
            else {
                j = mid - 1;
            }
        }
        return -1;
    }
};


Writeup: Standard binary search formula for a standard binary search problem.

Complexity: Time = O(logn), Space = O(1)
