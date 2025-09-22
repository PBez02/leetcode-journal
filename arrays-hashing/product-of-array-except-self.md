Name: Peter Bezgoubov
Date: 22/09/2025
Problem: Product of Array Except Self

Original attempt (Complexity: Time = O(n), Space = O(1), but uses division):
class Solution {
public:
   vector<int> productExceptSelf(vector<int>& nums) {
       int sum = 1;
       int zeroCount = 0;
       for (int i = 0; i < nums.size(); i++) {
           if (nums[i] == 0) {
               zeroCount++;
               continue;
           }
           sum *= nums[i];
       }
       vector<int> answer;
       int temp = sum;
       for (int j = 0; j < nums.size(); j++) {
           if (zeroCount > 1) {
               answer.push_back(0);
           }
           else if (zeroCount == 1) {
               if (nums[j] == 0) {
                   answer.push_back(sum);
                   sum = temp;
               }
               else {
                   answer.push_back(0);
               }
           }
           else {
               answer.push_back(sum / nums[j]);
               sum = temp;
           }
       }
       return answer;
   }
};

Prefix/Suffix method (didn’t solve this on my own, watched the solution):
class Solution {
public:
   vector<int> productExceptSelf(vector<int>& nums) {
       int prefix = 1;
       int arraysize = nums.size();
       vector<int> answer(arraysize);
       for (int i = 0; i < arraysize; i++) {
           answer[i] = prefix;
           prefix *= nums[i];
       }
       int suffix = 1;
       for (int j = arraysize - 1; j >= 0; j--) {
           answer[j] *= suffix;
           suffix *= nums[j];
       }
       return answer;
   }
};

Writeup 1: For my solution we first find the total sum of the numbers in the array excluding the 0’s. We use a zeroCount variable to count how many zeros are exactly in the array (it’s important).

After which we compute our output which is dependant on how many 0’s are in the initial array. If there is more than 1, we know for a fact the whole output array will be all 0. If there is only one 0, then we simply put 0’s for all values except where the 0 is. If there is no 0’s we just compute the sum as per normal by dividing the total by the current placeholder.

Writeup 2: For the suffix/prefix solution. I will try my best to explain. We are simply computing the sum of the numbers before and after each digit in the array. We do 2 passes through the array, one computing the prefixes, then afterwards computing the suffixes. When you multiply the 2, you end up with the product of numbers before and after each placeholder. (Sorry for the short explanation, I am also still trying to wrap my head around this solution)

