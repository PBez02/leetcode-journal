class Solution {
public:
   int findDuplicate(vector<int>& nums) {
       int slow = 0;
       int fast = 0;
       while (true) {
           slow = nums[slow];
           fast = nums[nums[fast]];
           if (slow == fast) {
               break;
           }
       }
       int slow2 = 0;
       while (true) {
           slow = nums[slow];
           slow2 = nums[slow2];
           if (slow == slow2) {
               break;
           }
       }
       return slow;
   }
};


Writeup: This solution works in 3 parts. The first part is recognising this as a Linked List problem where each index in the array “points” to the next “node”. After this, we can find that duplicate elements would cause a cycle in our Linked List. 

The second part is using Floyd's algorithm to detect cycles in a Linked List. From this we can find the point where the slow and fast pointers intercept.

The last part is knowing the the distance from the beginning of the list to the point where the cycle begins, is the same distance to where the fast and slow pointers meet to the beginning of the cycle as well. So we just start another “slow2” pointer and advance it the same speed as slow. Eventually when they intercept, we know it will intercept at the start of the cycle which is our duplicate number.

This problem isn’t so interesting because if you don’t know Floyd’s algorithm you won't really be able to solve it.

Complexity: Time = O(n), Space = O(1)
