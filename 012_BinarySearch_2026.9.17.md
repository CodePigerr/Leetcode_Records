

Binary Search:

I haven’t practiced algorithms for quite a while, being obsessed with AI coding recently. Approaching graduation, I’ve woken up to the fact that I need solid skills myself. Time to restart my algorithm journey, starting with this simple problem.

(二分查找：

我已经有一段时间没练习算法了，最近一直沉迷于人工智能编程。随着毕业临近，我终于意识到自己也需要掌握扎实的技能。是时候重新开始我的算法之旅了，就从这个简单的问题入手吧。）

```cpp
class Solution {
public:
    int search(vector<int>& nums, int target) {
        int l = 0,r = nums.size();int mid = (l+r)>>1;
        while(r>l)
        {
            if(nums[mid] > target) {r=mid;mid = (l+r) >> 1;}
            else if(nums[mid] < target){l = mid + 1;mid =(l+r) >> 1;}
            else if(nums[mid] == target)return mid;
            else return -1;
        }
        return -1;
    }
};
```

Perhaps there is not much to elaborate on. After a long period of accumulation, easy problems no longer pose a challenge to me. I can readily achieve fairly good time complexity.

(或许没什么好说的，经过了长时间沉淀，简单题对我而言已经没有挑战性了，可以较为轻松的得到相当不错的时间复杂度。）
