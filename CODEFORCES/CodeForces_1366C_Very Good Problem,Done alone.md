 # Concept : Zigzag fashioned path should be same, the middle zigzag can be ignored !!!

 ![Illustration](https://media.geeksforgeeks.org/wp-content/uploads/zigzag-1.png)

    #include <bits/stdc++.h>
    #include <ext/pb_ds/assoc_container.hpp>
    #include <ext/pb_ds/tree_policy.hpp>
    #define ll long long int
    #define ld long double
    #define pb push_back
    #define pll pair<ll, ll>
    #define vl vector<ll>
    #define vvl vector< vector<ll> >
    #define vlp vector< pair<ll, ll> >
    #define vllp vector<pair<pll, ll> >
    #define mll map<ll, ll>
    #define rep(i,a)  for(ll i=0; i< a; i++)
    #define rep1(i,a)   for(ll i = 1; i< a; i++)
    #define foi(i, a, b)    for(ll i = a; i<b ; i++)
    #define fod(i, a, b)    for(ll i = a; i>=b ; i--)
    #define mp make_pair
    #define all(v)  (v).begin(), (v).end()
    #define fst first
    #define sec second
    #define ff first.first
    #define fs first.second
    #define max3(a, b, c)   max(max(a, b), c)
    #define min3(a, b, c)   min(min(a, b), c)
    #define MAX 1000001
    #define MOD 1000000007
    // #define MOD 998244353
    #define endl "\n"
    #define INF (ll)1e18
    #define s(v) (ll)v.size()
    #define e(v) v.empty()
    #define bscount(x) __builtin_popcountll(x)
    // #define ordered_set tree<int, null_type,less<int>, rb_tree_tag,tree_order_statistics_node_update>

    using namespace std;
    // using namespace __gnu_pbds;



    int main(){

        ios::sync_with_stdio(0);
        cin.tie(0); cout.tie(0);

        ll t;
        ll null = 0;
        cin >> t;
        while(t--)
        {
             ll ROW,COL,i,j;
             cin >> ROW >> COL;
             ll a[ROW][COL];
             for(i=0;i<ROW;i++)
             {
                 for(j=0;j<COL;j++)
                 {
                     cin >> a[i][j];
                 }
             }
             ll line;
             ll z[ROW+COL],o[ROW+COL];
             z[0] = 0;
             o[0] = 0;
            foi(line,1,ROW+COL)
            {
              ll start_col = max(null,line-ROW);
              ll count = min(min(line,(COL-start_col)),ROW);
              z[line] = 0;
              o[line] = 0;
              foi(j,0,count)
              {
                  if(a[min(ROW, line)-j-1][start_col+j]==0)
                    z[line]++;
                  else
                    o[line]++;
              }
            }
            ll k = ROW+COL;
            ll ans = 0;
            for(line=1;line<=(k-1)/2;line++)
            {
                ans += min((z[line]+z[k-line]),(o[line]+o[k-line]));
            }
            cout << ans << endl;
        }
    }
