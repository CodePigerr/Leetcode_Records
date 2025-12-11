**Search Insert Position**

Emmm, it’s way too easy. Just treat it as a day off. Keep practicing every day without interruption, and you’ll get better over time.

This is a straight-up basic binary search template problem. It’s the most standard template-based question—no need to modify a single thing at all.

（搜索插入位置：

emmm过于简单，就当放松一天，只要每日不断，坚持下去就能变强。

这题直接基础二分模板。最标准的模板题，完全不需要改动任何东西。

）

```cpp
class Solution {
public:
    int searchInsert(vector<int>& nums, int target) {
        int l = 0;
        int r = nums.size();
        while(l < r)
        {
            int mid = l + (r-l)/2 ;
            if(nums[mid] >= target) r = mid; 
            else l = mid + 1;
        }
        return l;
    }
};
```

