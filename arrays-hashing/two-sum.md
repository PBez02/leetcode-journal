Name: Peter Bezgoubov
Date: 21/09/2025
Problem: Two Sum

class Solution {
public:
   vector<int> twoSum(vector<int>& nums, int target) {


       unordered_map<int, int> hashmap; // Initialise hashmap
       for (int i = 0; i < nums.size(); i++) { // Loop through array
           int complement = target - nums[i]; // Find complement
           if (hashmap.contains(complement)) { // Hash map has complement?
               return {hashmap[complement], i}; // Return indexes
           }
           else {
               hashmap[nums[i]] = i; // If not, store into hashmap
           }
       }
       return {}; // If no solution return no index
   }
};

Writeup: Straightforward. We create a hashmap storing the current number in the array and its index. We loop through the array and find out what the complement is. Example: if target is 9, we take our current number in the array and perform 9 - current number. We check if that complement is in our hashmap, if it isn’t we store the current number into the hashmap and move on until we find a match.

Complexity: Time = O(n), Space = O(n)
