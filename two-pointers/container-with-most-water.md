Name: Peter Bezgoubov
Date: 25/09/2025
Problem: Container with Most Water

class Solution {
public:
   int maxArea(vector<int>& heights) {
       int i = 0;
       int j = heights.size() - 1;
       int total_area = 0;
       int curr_area = 0;
       while (i < j) {
           if (heights[i] <= heights[j]) {
               curr_area = (j - i) * heights[i];
               i++;
           }
           else {
               curr_area = (j - i) * heights[j];
               j--;
           }
           if (curr_area > total_area) {
               total_area = curr_area;
           }
       }
       return total_area;
   }
};


Writeup: This one is another classic 2 pointers problem. We basically start with each pointer at the beginning and end of the array. We continuously check the area of water they create. If it’s greater than our total so far, we change the total. We only increment the pointer of the smaller “tower”. This may not make sense but lets say if our first tower is 1 but our last tower is 8, there may exist a tower in the array that is also 8 which is far greater than the area that 1 and 8 produce. Hence why we have to move the pointer which is pointing to 1.

Complexity: Time = O(n), Space = O(1)
