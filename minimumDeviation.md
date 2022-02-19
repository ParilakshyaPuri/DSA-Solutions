### APPROACH
```
It's a simple question that can be done by using only arrays. 
- First sort the array (a) and if a[0]%2 == 1 then a[0]*=2.
- and if a[n-1]%2 == 0 then a[n-1]/=2. make a variable d = a[n-1]-a[0];
- Keep updating d as, d= min(d, a[n-1]-a[0]).
But in this question, the constraints state- 1 <= nums[i] <= 109
So, we'll get a TLE if we use arrays, therefore we'll use set instead. 
```

### SOLUTION:
```
int minimumDeviation(vector<int>& nums) {
        //sort(nums.begin(), nums.end());
        set<int>  s;
        int n = nums.size();
        for(int i=0; i<n; i++){
            if(nums[i]%2 == 0){
                s.insert(nums[i]);
            }
            else{
                s.insert(nums[i]*2);
            }
        }
        int d = *s.rbegin() - *s.begin();
        while(*s.rbegin()%2 == 0){
            int x = *s.rbegin();
            s.erase(x);
            s.insert(x/2);
            d = min(d, *s.rbegin() - *s.begin());
        }
        return d;
    }
```
***Hope it helps!!🌞***
