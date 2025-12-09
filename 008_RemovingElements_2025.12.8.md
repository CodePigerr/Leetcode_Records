Removing Elements:

 Alright, shameless as ever, I reach for a familiar tool right off the bat: the almighty STL vector's remove paired with erase. 

Sure enough, the time complexity hit 100% [on LeetCode/online judge]. 

Then I took a moment to really think about the problem—removing all occurrences of a specific element... 

Isn't this just a simplified version of removing duplicates... 

I tried solving it with the fast and slow pointer technique, and sure enough, it worked like a charm.

(移除元素：

OK，依旧不知廉耻的开局就用已有工具：万能的STL vector的remove搭配erase。

然后时间复杂度果然100%，接下来开始思考时间，仔细看看题目，移除某一种相同元素。。。

这不就是删除重复项的简化操作吗。。。尝试快慢指针解决。果然没错。

)

1:

```cpp
class Solution {
public:
    int removeElement(vector<int>& nums, int val) {
        int tmp = 0;
        for(int i = 0; i < nums.size(); i ++)
            if(nums[i] != val) tmp++;
        auto p = std::remove(nums.begin(), nums.end() ,val);
        nums.erase(p, nums.end());
        return tmp;
    }
};
```



2:

```cpp
class Solution {
public:
    int removeElement(vector<int>& nums, int val) {
        int j = 0;
        for(int i = 0; i < nums.size(); i ++)
            if(nums[i] != val) nums[j ++] = nums[i];
        return j;
    }
};
```

Have to say, there are so many ways to use two pointers. The legend who invented pointers was a total genius!

（ 不得不说，双指针的玩法太多了，发明指针的大佬真是天才）