total no of tree possible for given max height h is - <br>
 b(h,n)=∑i=1:n b(h−1,i−1)⋅b(h−1,n−i) <br>
 <span>
Note that we have b(0,0)=1, b(0,1)=1 and b(0,k)=0, for any integer k>1 and  b(k,0)=1 k>0, which takes care of boundary conditions.
</span><br>
 Note: we are not considering permutation of nodes <br>
```
#include<bits/stdc++.h>
using namespace std;

#define ll long long 

const int mod = 1000000007;


int main()
{
ios_base::sync_with_stdio(0); 
cin.tie(0); cout.tie(0);
    
    int n;
    cin>>n;
    int l,r; ll ans;
    cin>>l>>r;
    vector<vector<ll>> v(r+1);
    for(int i=0;i<=r;i++){
        v[i].resize(n+1);
    }
    if(n==1){
        if(l>1)
        ans=0;
        else
        ans=1;
    }
    else{
        //first row
        for(int i=0;i<=n;i++){
            if(i==0 || i==1)
            v[0][i]=1;
            else
            v[0][i]=0;
        }
        //first column
        for(int i=0;i<=r;i++){
            v[i][0]=1;
        }
        int i=1;
        while(i<=r){
            for(int j=1;j<=n;j++){
                v[i][j]=0;
                for(int k=1;k<=j;k++){
                    v[i][j] = ( (v[i-1][k-1]*v[i-1][j-k])%mod + (v[i][j])%mod )%mod;
                }
            }
            i++;
        }
        
        if(l==1)
        ans= v[r-1][n];
        else
        ans = v[r-1][n]-v[l-2][n];
    }
    // for(int i=0;i<=r;i++){
    //     for(int j=0;j<=n;j++)
    //     cout<<v[i][j]<<" ";
    //     cout<<endl;
    // }
    // cout<<v[r][n]<<" "<<v[l][n]<<endl;
   
    cout<<ans;
    
return 0;
}



```
