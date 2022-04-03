### Problem Link: https://leetcode.com/problems/merge-intervals/

## Solution: (In Place merge)

> This solution includes optimization on space to modify the input itself where you can directly merge in-place. 
> We could keep track of length of sorted sub-list in intervals in an variable r (right end of sorted list formed till now). 

## CODE:
```
class Solution {
public:
    vector<vector<int>> merge(vector<vector<int>>& intervals) {
        sort(begin(intervals), end(intervals));
        int r = 0;
        for(auto i : intervals)
            if(i[0] <= intervals[r][1])                          
                intervals[r][1] = max(intervals[r][1], i[1]);
            else                                              
                intervals[++r] = i;
        intervals.resize(r+1);
        return intervals;

    }
};
```

**Hope this helps! if it does, kindly ⭐ it, that'll motivate me to make more of such posts!! 🌈🌞**
