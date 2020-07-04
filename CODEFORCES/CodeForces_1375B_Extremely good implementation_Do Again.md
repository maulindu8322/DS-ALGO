    #include <bits/stdc++.h>
    using namespace std;
    typedef long long ll;

    int main() {
      ios::sync_with_stdio(0); cin.tie(0);
      int t; cin >> t;
      while(t--) {
        int n, m; cin >> n >> m;
        int a[n+1][m+1];
        bool ok = 1;
        for(int i = 0; i < n; i++) {
          for(int j = 0; j < m; j++) {
            cin >> a[i][j];
            int mx = 4;
            if(i == 0 || i == n-1) mx--;
            if(j == 0 || j == m-1) mx--;
            if(a[i][j] > mx) ok = 0;
          }
        }
        if(!ok)
          cout << "NO" << '\n';
        else {
          cout << "YES" << '\n';
          for(int i = 0; i < n; i++) {
            for(int j = 0; j < m; j++) {
              int mx = 4;
              if(i == 0 || i == n-1) mx--;
              if(j == 0 || j == m-1) mx--;
              cout << mx << ' ';
            }
            cout << '\n';
          }
        }
      }
      return 0;
    }
