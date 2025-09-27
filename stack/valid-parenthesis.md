Name: Peter Bezgoubov
Date: 27/09/2025
Problem: Valid Parenthesis

class Solution {
public:
    bool isValid(string s) {
         stack<char> stackz;
         unordered_map<char, char> closeToOpen = {
            {')', '('},
            {']', '['},
            {'}', '{'}
         };


         for (char c : s) {
            if (closeToOpen.count(c)) {
                if (!stackz.empty() && stackz.top() == closeToOpen[c]) {
                    stackz.pop();
                }
                else {
                    return false;
                }
            }
            else {
                stackz.push(c);
            }
         }
         return stackz.empty();
    }
};

Writeup: This is a stack problem so we have to make a stack. We also have to make a hash map which maps each closed brace to its open brace.

We loop through each char inside the string. We first check if it is a closed or open brace. If it is an open brace, we straight push it to the stack. If not, we then do another check.

We check if the stack is empty, if it is empty we already know it’s invalid and we can return false. If not empty, we then check if the current top value in the stack matches the current open brace. If it match we can then pop the value on the top of stack and continue. If it doesn’t match we return false

Complexity: Time = O(n), Space = O(n)
