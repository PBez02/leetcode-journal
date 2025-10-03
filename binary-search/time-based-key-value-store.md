Name: Peter Bezgoubov
Date: 03/10/2025
Problem: Time Based Key-Value Store

class TimeMap {
public:
   unordered_map<string, vector<pair<int, string>>> storage;


   TimeMap() {
      
   }
  
   void set(string key, string value, int timestamp) {
      storage[key].push_back({timestamp, value});
   }
  
   string get(string key, int timestamp) {
       auto& values = storage[key];
       int left = 0;
       int right = values.size() - 1;
       string result = "";
       while (left <= right) {
           int mid = (left + right) / 2;
           if (values[mid].first <= timestamp) {
               result = values[mid].second;
               left = mid + 1;
           }
           else {
               right = mid - 1;
           }
       }
       return result;
   }
};


Writeup: This one looks tricky but is actually quite simple. It’s only the setup that is hard. So you first create a map which maps each key to an array for pair values. In the pair we have our value and our timestamp, in the example its {1, “happy”}. So we simply just create the map and for our set function, we just store the pair according to its key.


For get, we have to first store the key’s array into a variable called values. We then set up our binary search for this array. We search the array and if mid is less than our equal to timestamp, we set our result to the current pair's value. We then progress to the right half of the array to see if there is a closer timestamp in the array. If the current pair integer is less than timestamp, we know we must search the left half of the array. We continue this search and if there are no timestamps at all we just return an empty string.

Complexity: Time = O(1) for set, O(logn) for get. Space = O(m * n)
