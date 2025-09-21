Name: Peter Bezgoubov
Date: 21/09/2025
Problem: Valid Palindrome

#include <cctype>


class Solution {
public:
   bool isPalindrome(string s) {
       int i = 0; // First pointer index
       int j = s.size() - 1; // Second pointer


       while (i < j) {
           while (i < j && !(isalnum(s[i]))) { // Skip over non alnum
               i++;
           }
           while (i < j && !(isalnum(s[j]))){
               j--;
           }
           if (std::tolower(s[i]) != std::tolower(s[j])) { // Do they equal?
               return false; // If not return false
           }
           i++; // Increase left pointer
           j--; // Decrease right pointer
       }
       return true; // If no issue, return true
   }
};

Writeup: This is a classic 2 pointers problem. We basically just set the first pointer to the beginning of the string and one at the end. We then make the traverse the whole string up until the left pointer is no longer smaller than the right cross each other, for example:

r  a  c  e  c  a  r
P1                  P2 
r  a  c  e  c  a  r
  P1           P2
r  a  c  e  c  a  r
      P1    P2
r  a  c  e  c  a  r
          P1
          P2 (i = 3, j = 3, end the loop)

If there are any non alphanumeric characters we just continue to increase the index until we reach an alphanumeric character. We also convert all characters to lowercase before we check if they are the same. If at any point the 2 characters at both indexes don’t equal, we know it’s not a palindrome and return false. If we traverse the whole string with no issue, we know it is in fact a palindrome.

Complexity: Time = O(n), Space = O(1)
