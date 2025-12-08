### Removing Duplicates from a Sorted Array:

At first, I immediately thought of leveraging the features of `vector` and using iterators to erase elements at specified positions.

Later, I found that the space complexity of this approach was O(n), and it got a 100% acceptance rate on LeetCode.

But then I took a second thought and realized I could use the two-pointer technique for comparison. I gave it a try—if I didn’t miscalculate, the time complexity of this method should be O(1), right?

（删除有序数组中的重复项：

一开始直接就想到vector的特性用迭代器删去指定位置的元素。

然后发现空间复杂度就是O（n）了，力扣判定是100%。

但是后面想了一下，可以用双指针作比较，尝试了一下时间复杂度的量级应该是O（1）吧？没算错的话。

）

1:

```cpp
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        int last = -101;
        int tmp = nums.size();

        for(int i = nums.size() - 1; i >= 0; i --)
        {
            if(nums[i] == last)
            {
                nums.erase(nums.begin() + i);
                tmp --;
            }
            else 
            {
                last = nums[i];
            }
        }
        return tmp;
    }
};
```

2:

```cpp
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        if (nums.empty()) return 0;
        int s = 0;
        for (int f = 1; f < nums.size(); f ++) 
            if (nums[f] != nums[s]) 
                nums[++ s] = nums[f];
        return s + 1;
    }
};
```

