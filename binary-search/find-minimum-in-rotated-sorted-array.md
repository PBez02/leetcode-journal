Name: Peter Bezgoubov
Date: 30/09/2025
Problem: Find Minimum in Rotated Sorted Array

class Solution {
public:
   int findMin(vector<int> &nums) {
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
       return nums[i];
   }
};


Writeup: Our array can be divided into 2 separate portions if it is rotated. The left ascending portion and the right ascending portion. The maximum value of the right portion will always be less than the minimum value of the left portion. With these we can set up our binary search. 

We know the minimum value is where the left value is greater and the right value is greater. We set our first “if” condition that if mid is greater than the max value of the right portion (the last value of the array) then we know we are in the left portion of the array and need to search the right side. However if not, then we know we are in the right portion of the array and need to go left. We continue until we reach our minimum value and thus return it.

Complexity: Time = O(n), Space = O(1)
