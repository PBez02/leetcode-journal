Name: Peter Bezgoubov
Date: 21/09/2025
Problem: Group anagrams

class Solution {
public:
   vector<vector<string>> groupAnagrams(vector<string>& strs) {
       unordered_map<string, vector<string>> hashmap;
       for (int i = 0; i < strs.size(); i++) {
           string s = strs[i];
           vector<int> count(26, 0);
           for (int j = 0; j < s.size(); j++) {
               count[s[j] - 'a']++;
           }
           string res;
           for (int k = 0; k < 26; k += 1) {
               res += to_string(count[k]) + "#";
           }
           hashmap[res].push_back(s);
       }
       vector<vector<string>> answer;
       for (auto &kv : hashmap) {
           answer.push_back(kv.second);
       }
       return answer;
   }
};

Writeup: Okay this one was a little complicated. Once again we use our beloved hash map. Each string in the list input array has a unique combination of characters. Meaning for the word “eat” there is 1 e, 1 a and 1 t. We can use this info to group our anagrams. 

Firstly, we construct our hashmap. With the key being the unique combination string (we have to use string because hashmap doesn’t support an array of integers) and the value being the string itself. We create a for loop to go through the array of strings. Then we store the current string in an array and proceed to create a for loop to check each individual character as well. We also create our frequency array to distinguish how many characters of each letter are present. The word “eat” will look like this: 

[1, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0] (note any anagram of eat will also look like this, e.g. ate will also look like this, hence why we use a hashmap)

We then want to convert this into a string and store it in our hashmap by using the push_back function. It is important to space out each number with something for example a “#”, this is to differentiate the numbers. If we don’t do this, we wont be able to tell the difference between:

111, 1, 0, 0 and 11, 11, 0, 0 because a string they are both 111100

 Once we complete this process our hashmap should for example look like this:

hashmap = {
   "1#1#0#0...#" : ["cat", "act"],
   "1#0#0#1...#" : ["hat"],
   "1#1#0#1...#" : ["pots", "stop", "tops"]
}

Each anagram is tagged to a unique string value, and the string themselves are stored in the values column. After this, we simply print out the string with the ending for loop by pushing it into our answer vector<vector<>>.

Complexity: Time = O(m * n), Space = O(m * n)
