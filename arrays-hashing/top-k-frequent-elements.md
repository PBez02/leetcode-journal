Name: Peter Bezgoubov
Date: 21/09/2025
Problem: Top K Frequent Elements

class Solution {
public:
   vector<int> topKFrequent(vector<int>& nums, int k) {
       unordered_map<int, int> hashmap;
       for (int i = 0; i < nums.size(); i++) {
           hashmap[nums[i]]++;
       }


       vector<pair<int, int>> vec(hashmap.begin(), hashmap.end());
       sort(vec.begin(), vec.end(), [](auto &a, auto &b) {
           return a.second > b.second;
       });


       vector<int> answer;
       for (int j = 0; j < k; j ++) {
           answer.push_back(vec[j].first);
       }
      
       return answer;
   }
};

Writeup: This one is actually straightforward, it’s just the syntax that made it hard. We first create a frequency hashmap which will store each number as the key and how many times it has appeared in the area as the value. We then store this hashmap into a vector int pair (this is because hashmaps don’t have any sorting functions). So now our vector int pair will look like this for example:

[(5,4), (1,3), (3,2), (4,1)]

We then want to sort this vector in descending order from most frequent element to list frequent.

After this we simply just create our answer vector and push the most frequent element into our answer. We do this k times to get the k most frequent elements.

Complexity: Time = O(n), Space = O(n)
