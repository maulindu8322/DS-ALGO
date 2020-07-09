# Given a list of non negative integers, arrange them in such a manner that they form the largest number possible.The result is going to be very large, hence return the result in the form of a string.

# Input:
The first line of input consists number of the test cases. The description of T test cases is as follows:
The first line of each test case contains the size of the array, and the second line has the elements of the array.

# Output:
In each separate line print the largest number formed by arranging the elements of the array in the form of a string.

# Constraints:

1 ≤ T ≤ 100
1 ≤ N ≤ 102
0 ≤ A[i] ≤ 103

# Example:
## Input:

- 2
- 5
- 3 30 34 5 9
- 4
- 54 546 548 60

## Output:

- 9534330
- 6054854654


        #include <bits/stdc++.h>
        using namespace std;

        bool comp(string a,string b)
        {
            string x = a + b;
            string y = b + a;
            return (x>y)?1:0;
        }

        int main() {
          int t;
          cin >> t;
          while(t--)
          {
              int n,temp;
              cin >> n;
              vector<string> v;
              for(int i=0;i<n;i++)
              {
                  cin >> temp;
                  v.push_back(to_string(temp));
              } 
              sort(v.begin(),v.end(),comp);
              for(int i=0;i<v.size();i++)
              cout << v.at(i);
              cout << endl;
          }
          return 0;
        }
