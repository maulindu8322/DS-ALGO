        #include <bits/stdc++.h>
        using namespace std;

        void permute(string str, int l, int r)
        {
            if(l==r)
            {
                cout << str << " ";
                return;
            }
            else
            {
                for(int i=l;i<=r;i++)
                {
                    swap(str[l],str[i]);
                    sort(str.begin()+l+1,str.end());
                    permute(str,l+1,r);
                    swap(str[l],str[i]);
                }
            }
        }

        int main() {
          int t;
          cin >> t;
          while(t--)
          {
              string str;
              cin >> str;
              sort(str.begin(),str.end());
              int l = 0;
              int r = str.length();
              permute(str,l,r-1);
              cout << endl;
          }
          return 0;
        }
