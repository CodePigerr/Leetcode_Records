Palindrome Number:

Without using strings, you can use another integer (int) to extract the second half of the original number and compare it with the first half to get the answer.

（回文数：

在不使用字符串的情况下，使用另一个int类型的数字，获取原数字的后一半，与前一半进行比较即可获得答案。）

```cpp
class Solution {
public:
    bool isPalindrome(int x) {
        if (x < 0) return false;
        if (x != 0 && x % 10 == 0) return false;
        int y = 0;
        int n = 1;
        while(x > y)
        {
            y = y * 10 + x % 10;
            x /= 10;
        }
        return x == y || x == y / 10;
    }
};
```

