**Longest Common Prefix Sum**:

The problem requires given a vector of string arrays, find the minimum prefix sum within it. My first thought was to directly sort the array, then compare the smallest and largest elements.

(最长公共前缀和：

题目要求是给一个vector的string数组，在里面找最小前缀和。然后我第一时间想到的就是直接排序，取最小的和最大的作比较。

)

```cpp
class Solution {
public:
    string longestCommonPrefix(vector<string>& strs) {
        int n = strs.size();
        sort(strs.begin(), strs.end());
        string ans = "";
        for(int i = 0; i < strs[0].size(); i++)
        {
            if(strs[0][i] == strs[n - 1][i]) ans += strs[0][i];
            else break;
        }
        return ans;
    }
};
```

