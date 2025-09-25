Name: Peter Bezgoubov
Date: 25/09/2025
Problem: Trapping Rain Water

class Solution {
public:
   int trap(vector<int>& height) {
       if (height.size() == 0) {
           return 0;
       }
       int l = 0;
       int r = height.size() - 1;
       int leftMax = height[l];
       int rightMax = height[r];
       int total_water = 0;
       while (l < r) {
           if (leftMax < rightMax) {
               l++;
               leftMax = max(leftMax, height[l]);
               total_water += leftMax - height[l];
           }
           else {
               r--;
               rightMax = max(rightMax, height[r]);
               total_water += rightMax - height[r];
           }
       }
       return total_water;
   }
};


Writeup: I did not get this without looking at the solution. It’s funny because the code is so short. We basically keep track of 2 things, our right max and our left max. We know with whatever index we are at right now, we are bound by these 2 heights. So at each index we simply just take the height of our smaller boundary (either left or right max) and then take the max and subtract it by the height. This gives us how much water we can store at each index.

For example if leftMax is < rightMax, we know we must use leftMax to compute the water because it’s the smaller boundary. Vice versa with rightMax.

Complexity: Time = O(n), Space = O(1)
