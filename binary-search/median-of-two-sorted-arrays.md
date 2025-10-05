Name: Peter Bezgoubov
Date: 05/10/2025
Problem: Median of Two Sorted Arrays

Median of Two Sorted Arrays

class Solution {
public:
   double findMedianSortedArrays(vector<int>& nums1, vector<int>& nums2) {
       vector<int>& A = nums1;
       vector<int>& B = nums2;


       int total = A.size() + B.size();
       int half = (total + 1) / 2;


       if (B.size() < A.size()) {
           swap(A, B);
       }


       int l = 0;
       int r = A.size();
       while (l <= r) {
           int i = (l + r) / 2;
           int j = half - i;


           int Aleft = i > 0 ? A[i-1] : INT_MIN;
           int Aright = i < A.size() ? A[i] : INT_MAX;
           int Bleft = j > 0 ? B[j-1] : INT_MIN;
           int Bright = j < B.size() ? B[j] : INT_MAX;


           if (Aleft <= Bright && Bleft <= Aright) {
               if (total % 2 != 0) {
                   return max(Aleft, Bleft);
               }
               return (max(Aleft,Bleft) + min(Aright, Bright)) / 2.0;
           }
           else if (Aleft > Bright) {
               r = i - 1;
           }
           else {
               l = i + 1;
           }
       }
       return -1;
   }
};


Writeup: To find the median of any list, it can be broken down into 2 partitions, the left and the right. When we have an odd sized list, we just take the middle value between these 2 partitions, when we have an even size list, we take the max value of the left partition and the minimum value of the right partition and add them and divide by 2.

The way this algorithm works is it builds our left partition. We do this by finding the smaller array of the 2 (if it’s the same size it doesn’t matter) and store it into the pointer A. We then perform a search on the array A.  We take the midpoint of A and the total size of both arrays. E.g. lets say our total size is 12 but our array A is only size 6, then we take the first half of A and the first 3 values of B (3 + 3 = 6, midpoint of total). We then settle some edge cases where either array is empty. We create our values Aleft and Aright, Bleft and Bright which signify the 2 values on the left and right of each midpoint.

For example if array A is [1, 2, 3, 4] and B is [1, 2, 3, 4, 5, 6, 7, 8]. Aleft would 2, Aright would 3. B left would be 4, and Bright would be 5.

Now we can begin our computation. We check if the left partition is successful by check if Aleft is less than Bright and if Bleft is less than Aright, if this is the case, we know our partition is in order and we can proceed to compute the median.

However, if Aleft is greater than Bright, we know we need to increase the size of the partition in A and decrease the partition size in B, thus we adjust our pointers accordingly. It’s the same the other way, if Bleft is greater than Aright, we know the partition size of B must be greater than A so we must adjust the pointers accordingly.

Complexity: Time = O(log(min(m + n))) Space = O(1)
