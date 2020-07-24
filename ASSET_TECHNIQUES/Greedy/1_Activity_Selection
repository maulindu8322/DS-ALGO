 # Main concept : Crux :
 
  ### This method tells number of work without any clash
 
 Link : [Leetcode 452](https://leetcode.com/problems/minimum-number-of-arrows-to-burst-balloons/)
 
      
      class Solution {
      public:
          static bool comp(vector<int>&a,vector<int>&b)
          { 
              if(a[1]==b[1]) return a[0]<=b[0];
              return a[1]<b[1];
          }

          int findMinArrowShots(vector<vector<int>>& a) {
              if(a.size()==0) return 0;
              sort(a.begin(),a.end(),comp);
              int n = a.size();
              int ans = 1;
              int f = a[0][1];
              for(int i=1;i<n;i++)
              {
                  if(a[i][0]>f)
                  {
                      ans++;
                      f = a[i][1];
                  }
              }
              return ans;

          }
      };
