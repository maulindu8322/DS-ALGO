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
          #define PI 3.1415926535897932384626
          // #define MOD 998244353
          #define endl "\n"
          #define INF (ll)1e18
          #define s(v) (ll)v.size()
          #define e(v) v.empty()
          #define bscount(x) __builtin_popcountll(x)
          /**
           * Limits in C++ for reference
           * _____________________________________________________________________________________
           * |Sr| Macro Name | Description                     | Value
           * |No|____________|_________________________________|__________________________________
           * |1.| ULLONG_MAX | Maximum value unsigned long long| 18,446,744,073,709,551,615 (10^20)
           * |2.| LLONG_MAX  | Maximum value long long         | 9,223,372,036,854,775,807 (10^19)
           * |3.| LLONG_MIN  | Minimum value long long         |-9,223,372,036,854,775,808 -1*(10^19)
           * |4.| INT_MAX    | Maximum value int               | 2,147,483,647 (10^10)
           * |5.| INT_MIN    | Minimum value int               |-2,147,483,648 (10^10)
          */
          // #define ordered_set tree<int, null_type,less<int>, rb_tree_tag,tree_order_statistics_node_update>

          using namespace std;
          // using namespace __gnu_pbds;



          int main(){

              ios::sync_with_stdio(0);
              cin.tie(0); cout.tie(0);


              ll n,i;
              cin >> n;
              ll a[n],b[n];
              foi(i,0,n)
              {
                  cin >> a[i];
              }
              foi(i,0,n)
              {
                  cin >> b[i];
              }
              map<ll,ll> mpa,mpb;
              foi(i,0,n)
              {
                  mpa.insert(pll(a[i],i));
                  mpb.insert(pll(b[i],i));
              }
              vector<ll> v;
              for(auto ita=mpa.begin();ita!=mpa.end();ita++)
              {
                  auto itb = mpb.find(ita->first);
                  if(itb->second>=ita->second) 
                      v.pb(itb->second-ita->second);
                  else
                      v.pb(n-abs(itb->second-ita->second));
              }
              map<ll,ll> mpc;
              foi(i,0,v.size())
              {
                  if(mpc.find(v[i])!=mpc.end())
                      mpc[v[i]]++;
                  else
                      mpc.insert(pll(v[i],1));
              }
              ll ans = 0;
              for(auto itc=mpc.begin();itc!=mpc.end();itc++)
                  ans = max(ans,itc->second);
              cout << ans << endl;
          }
