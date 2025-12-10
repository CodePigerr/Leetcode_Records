Character matching:

Let's continue with the brute-force solution using double pointers, and then consider the KMP algorithm.

After using double pointers a lot, I feel like they can solve almost any problem.

（字符匹配：

继续，双指针暴力解，然后再考虑KMP算法。

双指针用多了感觉有一种能解万物的感觉。

）

```cpp
class Solution {
public:
    int strStr(string haystack, string needle) {
        //暴力
        if (needle.empty() || needle.length() > haystack.length()) return -1;
        for(int i = 0; i <= haystack.length() - needle.length(); ++ i)
        {
            int j = 0;
            while(j < needle.length() && haystack[i + j] == needle[j]) j++;
            if(j == needle.length()) return i;
        }
        return -1;
    }
};
```



KMP:

```CPP
class Solution {
public:
    int strStr(string haystack, string needle) {
        //KMP
        if (needle.empty() || needle.length() > haystack.length()) return -1;
        vector<int> next(needle.length());
        for(int i = 1, j = 0; i < needle.length(); i ++)
        {
            while(j > 0 && needle[i] != needle[j]) j = next[j - 1];
            if(needle[i] == needle[j]) j ++;
            next[i] = j;
        }

        for(int i = 0, j = 0; i < haystack.length(); i ++)
        {
            while(j > 0 && haystack[i] != needle[j]) j = next[j - 1];
            if(haystack[i] == needle[j]) j ++;
            if(j == needle.length()) return i - needle.length() + 1;
        }
        return -1;
    }
};
```

In fact, I found that the method of calculating the `next` array and the optimized `nextval` array taught in the Wangdao 408 course is different from that in other online tutorials. Other tutorials focus on finding the **longest prefix-suffix** (the longest proper prefix which is also a suffix), while the Wangdao 408 course calculates the next position of different values. Maybe I haven't fully understood it yet. I will study it carefully and attach my insights when I check in tomorrow.

（事实上，我发现王道408课程教学的求next数组和nextval优化数组，和网上其他教程不一样。其他教程是找最长前缀和，王道408求解的是不同值的下一位，或许是我还没完全理解，之后会仔细看看，明天打卡时附上心得。）



