Name: Peter Bezgoubov
Date: 30/09/2025
Problem: Search in Rotated Sorted Array

class Solution {
public:
   int search(vector<int>& nums, int target) {
       int i = 0;
       int j = nums.size()-1;
       if (nums.size() == 0) {
           return -1;
       }
       while (i < j) {
           int mid = (i + j) / 2;
           if (nums[mid] > nums[j]) {
               i = mid + 1;
           }
           else {
               j = mid;
           }
       }
       int pivot = i;
       if (pivot == 0) {
           i = 0;
           j = nums.size()-1;
       }
       else if (nums[pivot] == target) {
           return pivot;
       }
       else if (target >= nums[0]) {
           i = 0;
           j = pivot - 1;
       }
       else {
           i = pivot;
           j = nums.size()-1;
       }
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


Writeup: This solution works by finding the minimum value in the array and setting it as the pivot. If our target is greater than the last value in the array, we know we must search to the left of the pivot. If not, search to the right of the pivot. We then conduct another binary search on either side of the pivot to find our target. If not target is not found, return -1.

Complexity: Time = O(n), Space = O(1)
