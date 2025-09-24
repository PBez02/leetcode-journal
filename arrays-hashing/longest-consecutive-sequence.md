Name: Peter Bezgoubov
Date: 24/09/2025
Problem: Longest Consecutive Sequence

class Solution {
public:
   int longestConsecutive(vector<int>& nums) {
       if (nums.size() == 0) {
           return 0;
       }
       unordered_map<int,int> hashmap;
       int max = nums[0];
       int min = nums[0];
       for (int i = 0; i < nums.size(); i++) {
           if (nums[i] > max) {
               max = nums[i];
           }
           if (nums[i] < min) {
               min = nums[i];
           }
       }
       for (int i = 0; i < nums.size(); i++) {
           hashmap[nums[i]] = i;
       }
       int total_score = 0;
       int curr_score = 0;
       int curr_num = min;
       while (curr_num <= max) {
           if (hashmap.count(curr_num)) {
               curr_score += 1;
               if (curr_score > total_score) {
                   total_score = curr_score;
               }
           }
           else {
               curr_score = 0;
           }
           curr_num += 1;
       }
       return total_score;
   }
};


class Solution {
public:
   int longestConsecutive(vector<int>& nums) {
       if (nums.size() == 0) {
           return 0;
       }
       unordered_set<int> set;
       for (int i = 0; i < nums.size(); i++) {
           set.insert(nums[i]);
       }
       int total_score = 1;
       int curr_score = 1;
       for (int j : set) {
           if (!set.count(j-1)) {
               int curr_num = j;
               curr_score = 1;
               while (set.count(curr_num + 1)) {
                   curr_score += 1;
                   curr_num += 1;
               }
           }
           if (curr_score > total_score) {
               total_score = curr_score;
           }
       }
       return total_score;
   }
};




Writeup 1: The first one was my solution of just taking the min and max of any array and then looping through finding sequence, but obviously this can be very slow because let’s say you have an array of [1, 1000000000]. You are gonna loop from 1 to 1000000000, even though n is only 2. The next solution is a lot more clever

Writeup 2: The faster solution is to just a set which gets rid of duplicate elements. After which, you know each sequence must start with a value. This value does not have a left neighbour. Meaning for sequence 1, 2, 3, 4. You can see there is no value to the left of 1. We check for this in our loop with if (!set.count(x-1)). Once we found a value with no left neighbour. We check the length of the sequence and store it in our total_score. If any sequence is longer than total_score we update it accordingly and return it in the end.

Complexity: Time = O(n), Space = O(n)
