Name: Peter Bezgoubov
Date: 21/09/2025
Problem: 3sum

class Solution {
public:
   vector<vector<int>> threeSum(vector<int>& nums) {
       sort(nums.begin(), nums.end());
       int end = nums.size() - 1;
       vector<vector<int>> answer;
       for (int i = 0; i < end - 1; i++) {
           if (i > 0 && nums[i] == nums[i-1]) { // duplicate check
               continue;
           }
           int j = i + 1;
           int k = end;
           while (j < k) {
               if (nums[i] + nums[j] + nums[k] == 0) {
                   answer.push_back({nums[i], nums[j], nums[k]});
                   while (j < k && nums[j] == nums[j+1]) { // duplicate check
                       j++;
                   }
                   while (j < k && nums[k] == nums[k-1]) { // duplicate check
                       k--;
                   }
                   j++;
                   k--;
               }
               else if (nums[i] + nums[j] + nums[k] > 0) {
                   k--;
               }
               else {
                   j++;
               }
           }
       }
       return answer;
   }
};

Writeup: This one is pretty tricky. You must first sort the array and make it into a 2 sum problem by fixing the first pointer (this is not really a 2 pointer problem, it's more like 3). So we fix the first pointer at the beginning of the array. Then our next pointers run a 2 sum solution on the remainder of the array. After it finds a valid 3 number combo that adds up to 0, we store it in our output vector.

The rest of the problem is just skipping duplicates, we use this with carefully constructed while loops at different stages of the loop.

Complexity: Time = O(n^2), Space = O(m)
