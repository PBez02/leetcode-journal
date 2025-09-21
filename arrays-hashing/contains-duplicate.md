Name: Peter Bezgoubpv
Date: 21/09/2025
Problem: Contains Duplicate

class Solution {
public:
   bool containsDuplicate(vector<int>& nums) {
       unordered_map<int, int> hashmap;
       for (int i = 0; i < nums.size(); i++) {
           if (hashmap.count(nums[i])) {
               return true;
           }
           hashmap[nums[i]] = i;
       }
       return false;
   }
};

Writeup: An even simpler and more straightforward one. We just pass through the array, and we check if the current number exists in our hash map, if it does, we return true. If we loop through the whole array it means there is no duplicate, thus returning false.

Complexity: Time = O(n), Space = O(n)
