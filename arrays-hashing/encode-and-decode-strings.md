Name: Peter Bezgoubov
Date: 22/09/2025
Problem: Enconde and Decode Strings

class Solution {
public:

    string encode(vector<string>& strs) {
        string s = "";
        for (int i = 0; i < strs.size(); i++) {
            s += strs[i] + "~";
        }
        return s;
    }

    vector<string> decode(string s) {
        int j = 0;
        vector<string> answer;
        while (s[j] != '\0') {
            string temp;
            while (s[j] != '~') {
                temp.push_back(s[j]);
                j++;
            }
            answer.push_back(temp);
            j++;
        }
        return answer;
    }
};

Writeup: This one may seem hard but is fairly simple. You just loop through the array of strings and everytime you append it to your accumulator string “s”, you add a separator that is a non ASCII character, in this case I used ‘~’. 

Once you get to decoding, you just loop through the string and collect the characters and store them into a temporary string. Once you hit the ‘~’ you know it’s the end of the word and then proceed to push that temporary string into your vector<string>. After which you simply continue until you are finished looping through the string.

Complexity: Time = O(m), Space = O(m + n)
