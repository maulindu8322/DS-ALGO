# Given an array(0-based indexing), you have to find the max sum of i*A[i] where A[i] is the element at index i in the array. The only operation allowed is to rotate(clock-wise or counter clock-wise) the array any number of times.

## Input:
- The first line of input is the number of test cases T. Then T test cases follow. The first line of each test case is an integer N denoting the size of the array. Then in the next line are N space separated values of the array A [ ]. 

## Output:
- For each test case, the output will be the required max sum in a new line.

## User Task:
 Your task is to complete the function max_sum which takes two arguments which is the array A [ ] and its size and returns an integer value denoting the required max sum.

## Expected Time Complexity: O(N).
## Expected Auxiliary Space: O(1).

## Constraints:
- 1<=T<=1000
- 1<=N<=104
- 1<=A[]<1000

## Example:
### Input
- 1
- 4
- 8 3 1 2
### Output
- 29

## Explanation
- Above the configuration possible by rotating elements are
- 3 1 2 8 here sum is 3*0+1*1+2*2+8*3 = 29
- 1 2 8 3 here sum is 1*0+2*1+8*2+3*3 = 27
- 2 8 3 1 here sum is 2*0+8*1+3*2+1*3 = 17
- 8 3 1 2 here sum is 8*0+3*1+1*2+2*3 =  11
- Here the max sum is 29 


# Solution : 
 
 This method discusses the efficient solution which solves the problem in O(n) time. In the naive solution, the values were calculated for every rotation. So if that can be done in constant time then the complexity will decrease.



## Approach: 

The basic approach is to calculate the sum of new rotation from the previous rotations. This brings up a similarity where only the multipliers of first and last element change drastically and the multiplier of every other element increases or decreases by 1. So in this way, the sum of next rotation can be calculated from the sum of present rotation.

## Algorithm: 

The idea is to compute the value of a rotation using values of previous rotation. When an array is rotated by one, following changes happen in sum of i*arr[i].
Multiplier of arr[i-1] changes from 0 to n-1, i.e., arr[i-1] * (n-1) is added to current value.
Multipliers of other terms is decremented by 1. i.e., (cum_sum - arr[i-1]) is subtracted from current value where cum_sum is sum of all numbers.


      next_val = curr_val - (cum_sum - arr[i-1]) + arr[i-1] * (n-1);
      next_val = Value of ∑i*arr[i] after one rotation.
      curr_val = Current value of ∑i*arr[i] 
      cum_sum = Sum of all array elements, i.e., ∑arr[i].



Lets take example {1, 2, 3}. Current value is 1*0+2*1+3*2 = 8. Shifting it by one will make it {2, 3, 1} and next value will be 8 - (6 - 1) + 1*2 = 5 which is same as 2*0 + 3*1 + 1*2


# Code : 

      // An efficient C++ program to compute
      // maximum sum of i*arr[i]
      #include<bits/stdc++.h>

      using namespace std;

      int maxSum(int arr[], int n)
      {
          // Compute sum of all array elements
          int cum_sum = 0;
          for (int i=0; i<n; i++)
              cum_sum += arr[i];

          // Compute sum of i*arr[i] for initial
          // configuration.
          int curr_val = 0;
          for (int i=0; i<n; i++)
              curr_val += i*arr[i];

          // Initialize result
          int res = curr_val;

          // Compute values for other iterations
          for (int i=1; i<n; i++)
          {
              // Compute next value using previous 
              // value in O(1) time
              int next_val = curr_val - (cum_sum - arr[i-1])
                             + arr[i-1] * (n-1);

              // Update current value
              curr_val = next_val;

              // Update result if required
              res = max(res, next_val);
          }

          return res;
      }

      // Driver code
      int main()
      {
          int arr[] = {8, 3, 1, 2};
          int n = sizeof(arr)/sizeof(arr[0]);
          cout << maxSum(arr, n) << endl;
          return 0;
      }
      
## Complexity analysis:

- Time Complexity: O(n).
- Since one loop is needed from 0 to n to check all rotations and the sum of the present rotation is calculated from the previous rotations in O(1) time).
- Auxiliary Space: O(1).
- As no extra space is required to so the space complexity will be O(1)
