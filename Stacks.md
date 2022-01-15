## Problem Link: https://www.codechef.com/LRNDSA04/problems/STACKS

<br>

## Solution: 
- For this question we need to use 1 STL operation upper_bound.
- upper_cound basically returns an iterator pointing to the first element in the range (first, last).
    - that is greater than value
    - or last if no such element is found. 
<br>
Let's move to the code:

```
#include<bits/stdc++.h>
#define ll long long
#define newl '\n';
using namespace std;
int main(){
	ll t; cin>>t;
	while(t--){
	    ll n; cin>>n;
	    ll a[n+1];
	    vector<ll> v;
	    for(ll i=0; i<n; i++){
	        cin>>a[i];
	    }
	   for(ll i=0; i<n; i++){
	       ll curr_disc= a[i];
	       auto it= upper_bound(v.begin(), v.end(), curr_disc);
	       if(it== v.end()){
	           v.push_back(a[i]);
	       }
	       else{
	           *it=a[i];
	       }
	   }
	   cout<<v.size()<<' ';
	   for(ll i=0; i<v.size(); i++){
	       cout<<v[i]<<' ';
	   }
	   cout<<newl; 
	}
	
	return 0;
}
```
