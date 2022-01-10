```
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
