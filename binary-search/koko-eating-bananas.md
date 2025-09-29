Name: Peter Bezgoubov
Date: 29/09/2025
Problem: Koko Eating Bananas

class Solution {
public:
    int minEatingSpeed(vector<int>& piles, int h) {
        int left = 1;
        int right = *max_element(piles.begin(), piles.end());
        int k = right;
        while (left <= right) {
            int mid = (left + right) / 2;
            long long total_time = 0;
            for (int pile : piles) {
                total_time += (pile + mid - 1) / mid;
            }
            if (total_time <= h) {
                k = mid;
                right = mid - 1;
            }
            else {
                left = mid + 1;
            }
        }
        return k;
    }
};


Writeup: This solution is actually easier to figure out once you try out the brute force solution. You first try setting k to 1, then seeing if it is less than or equal to h. If it isn’t, you keep incrementing k by 1 until you find your desired k value.

However, you know the maximum value of k has to be the value of the largest pile. Given this, you have your range set for k (1 <= k <= max of piles). With this, you can conduct your binary search within these boundaries until you have found your desired k. Making the total time (nlog(m)) where m is the max value.

Complexity: Time = O(nlog(m)), Space = O(1)
