### Problem Link: https://leetcode.com/problems/cherry-pickup-ii/

## Solution based on intuition!
Basic problem: 
- The robots need to collect maximum cherries.
- The robots can move in just 3 directions -> 
   - diagonal left
   - bottom
   - diagonal right
   
<hr>  

### Solution:
- we can see this is a DP problem, as it has optimal substructure, and it has similar sub-problems.
  #### let's breakdown the problems:
  - We need to decide the dimentions: it is decided on the basis of **parameters** that we pass to a **recursive function calls** *i.e if one parameter changing in the recursive calls then 1D, if two parameters are changing then 2D, if three then 3D.*
  - So, for this we need 3 dimentions.
  - **ROBOTS CAN MOVE SIMULTANEOUSLY!!!**

<hr>

### Possible movements!!!
- There are total 9 possible movements.
- In this r1=r2, meaning that both robots are moving down simultaneously. 

```
            dp[r - 1][c1 - 1][c2 - 1],
            dp[r - 1][c1 - 1][c2],
            dp[r - 1][c1 - 1][c2 + 1],
            dp[r - 1][c1][c2 - 1],
            dp[r - 1][c1][c2],
            dp[r - 1][c1][c2 + 1],
            dp[r - 1][c1 + 1][c2 - 1],
            dp[r - 1][c1 + 1][c2],
            dp[r - 1][c1 + 1][c2 + 1]
```
- We need to return the maximum of these moves, such that it results in maximum cherries. 

<hr>

### Incase there was a clash where robots are in same cell.
dp[r][c1][c2];

**HOW TO DECIDE WHICH ROBOT GETS THE CHERRIES?**
```
 if(c1==c2){
      cherry+=grid[r1][c1];
 }
else{
      cherry+=grid[r1][c1];
      cherry+=grid[r1][c2];
}
```
<hr>

## Combining all into the code!

```
class Solution {
public:
    int dp[71][71][71];

    int solve(vector<vector<int>>&grid,int r1,int c1,int c2){
        int r2=r1;
        // off limit conditions!
        if(r1>=grid.size() or r2>=grid.size() or c1<0 or 
           c2<0 or c1>=grid[0].size() or c2>=grid[0].size()){
            return INT_MIN;
        }
        // already computed values!
        if(dp[r1][c1][c2]!=-1){
            return dp[r1][c1][c2];
        }
        // landing onto the last row!!
        if(r1==grid.size()-1){
            if(c1==c2){
                return grid[r1][c1];
            }
            else{
                return grid[r1][c1]+grid[r1][c2];
            }

        }
        int cherry=0;
        // landing onto the same column!
        if(c1==c2){
            cherry+=grid[r1][c1];
        }
        else{
            cherry+=grid[r1][c1];
            cherry+=grid[r1][c2];
        }
        int maxcherry=0;
        for(int i=-1;i<=1;i++){
            for(int j=-1;j<=1;j++){
                maxcherry=max(maxcherry,solve(grid,r1+1,c1+i,c2+j));
            }
        }
        return dp[r1][c1][c2]=cherry+maxcherry;

    }
    
    
    int cherryPickup(vector<vector<int>>& grid) {
        int m=grid.size(), n=grid[0].size();
        memset(dp,-1,sizeof(dp));
        int ans=solve(grid,0,0,n-1);

        return ans;
    }
};
```
***Hope this helps! if it does, kindly star it, that'll motivate me to make more of such posts!!***
