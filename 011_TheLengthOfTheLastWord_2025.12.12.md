**The length of the last word:  **

Today’s problem is still an easy one—aren’t we being a bit too slack? Let’s move on to medium-difficulty problems after finishing the first round of Wangdao 408 and Advanced Mathematics by the end of January.

For this problem, the conventional approach is to traverse the string from start to finish. Whenever a space is encountered, the word length counter is reset to zero. That’s why we need a variable to store the length of the last recorded word, preventing cases where there is no word left at the end of the string.

Then there’s the reverse thinking approach: traverse the string from the end to the start. Once we finish traversing a complete word, the problem is solved. So adding a check for `len == 0` can reliably ensure that the counter is only reset when a space is encountered *after* a word. It also handles the scenario where there are no spaces at all—meaning we have traversed the entire string.

（最后一个单词长度：

今天依旧是简单题，是不是有点太懈怠了？等1月底学完王道408和高数一轮，开始上中等题吧。今天的题，正常思路是从头到尾遍历,遇到空格就会统计数字归零，所以需要一个变量统计上一次数据，防止后面没有单词。

然后反向思维，从尾部向头部遍历，只要遍历完一个单词就解决了。所以加了一个判断len == 0就能稳定保证，一定是遇到单词之后遇到空格才会归零，也有可能没有空格，那就遍历完了。

）

```cpp
class Solution {
public:
    int lengthOfLastWord(string s) {
        int ans, len = 0;
        for(int i = 0; i < s.length(); i ++)
            if(s[i] != ' '){len ++; ans = len;}
            else len = 0;
        return ans;
        }
};
```

```c++
class Solution {
public:
    int lengthOfLastWord(string s) {
        int ans, len = 0;
        for(int i = s.length() - 1; i >= 0; i --)
            if(s[i] == ' '){if(len == 0)continue;break;}
            else len ++;
        return len;
    }
};
```

