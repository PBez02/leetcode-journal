Name: Peter Bezgoubov
Date: 21/09/2025
Problem: Two Sum II (array is sorted)

class Solution {
public:
   vector<int> twoSum(vector<int>& numbers, int target) {
       int i = 0;
       int j = numbers.size() - 1;
       while (i < j) {
           if (numbers[i] + numbers[j] == target) {
               return {i+1, j+1};
           }
           else if (numbers[i] + numbers[j] > target) {
               j--;
           }
           else{
               i++;
           }
       }
       return {};
   }
};

Writeup: For this solution, we set 1 pointer at the start of the array and the other pointer to the end. We continuously check if the 2 numbers add up to the target. If the sum is greater, we know we must shift our right pointer down but if it is smaller we must shift our left pointer up. We continue this until we reach 2 numbers that equal our sum. If not we simply return the empty pair.

Complexity: Time = O(n), Space = O(1)

