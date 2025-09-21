Name: Peter Bezgoubov
Date: 21/09/2025
Problem: Valid anagram

class Solution {
public:
    bool isAnagram(string s, string t) {
        if (s.size() != t.size()) {
            return false;
        }
        unordered_map<char, int> hashmap1;
        unordered_map<char, int> hashmap2;
        for (int i = 0; i < s.size(); i += 1) {
            hashmap1[s[i]] += 1;
            hashmap2[t[i]] += 1;
        }
        if (hashmap1 == hashmap2) {
            return true;
        }
        return false;
    }
};

Writeup: There are 2 ways of doing this. The first way is to create 2 frequency arrays and just see if they match. The other way is creating 2 hashmaps for each string and then comparing them in the end. The keys column is each character and the value column is how many times this character has appeared in the string.

Complexity: Time = O(n), Space = O(n)
