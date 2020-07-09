 # Spirally traversing a matrix 
 
 ![Illustration](https://www.geeksforgeeks.org/wp-content/uploads/spiral-matrix.png)
 
 - cs : column start
 - ce : column end
 - rs : row start
 - re : row end
      
      
      
        #include <bits/stdc++.h>
        using namespace std;

        int main() {
            int t;
            cin >> t;
            while(t--)
            {
                int m,n,i,j;
                cin >> n >> m;
                int a[n][m];
                for(int i=0;i<n;i++)
                {
                    for(int j=0;j<m;j++)
                    {
                        cin >> a[i][j];
                    }
                }
                vector<int> v;
                int rs = 0;
                int re = n;
                int cs = 0;
                int ce = m;
                while(rs<re && cs<ce)
                {
                    for(int i=cs;i<ce;++i)
                    {
                        v.push_back(a[rs][i]);
                    }
                    rs++;

                    for(int i=rs;i<re;++i)
                    {
                        v.push_back(a[i][ce-1]);
                    }
                    ce--;

                    if(rs<re)
                    {
                        for(int i=ce-1;i>=cs;--i)
                        {
                            v.push_back(a[re-1][i]);
                        }
                        re--;
                    }

                    if(cs<ce)
                    {
                        for(int i=re-1;i>=rs;--i)
                        {
                            v.push_back(a[i][cs]);
                        }
                        cs++;
                    }
                }
                for(int i=0;i<v.size();i++)
                {
                    cout << v[i] << " ";
                }
                cout << endl;
            }

          return 0;
        }
