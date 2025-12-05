Valid Parentheses:

A brute-force approach using direct `if` conditions is actually the optimal solution.

However, after reading the official solution, I realized how "shit mountain code" (poorly designed, unmaintainable code) comes into being.

Overemphasis on performance optimization can lead to difficulties in subsequent maintenance. Once an error occurs, it becomes hard to debug and extend. When performance is roughly equivalent, readability should be the top priority. The following is the official solution for reference and learning.

（有效的括号：

直接if暴力解题，直接就是最优解。

但是看了官方题解之后，我知道屎山代码是怎么来的了。

过度关注性能优化，会导致后续维护困难，一旦有地方出错，不好维护，不好拓展，性能差不多的情况下，可读性才是最优选。后面的是官方题解，借鉴学习。）

```cpp
class Solution {
public:
    bool isValid(string s) {
        stack<char> m;
        for(int i = 0; i < s.length(); i ++)
        {
            if(s[i] == '{' || s[i] == '[' || s[i] == '(')
                m.push(s[i]);
            else if(m.empty()) return false;
            else if(s[i] == '}' && m.top() == '{')
                m.pop();
            else if(s[i] == ']' && m.top() == '[')
                m.pop();
            else if(s[i] == ')' && m.top() == '(')
                m.pop();
            else return false;
        }
        if(m.empty())return true;
        else return false;
    }
};
```

```cpp
class Solution {
public:
    bool isValid(string s) {
        int n = s.size();
        if (n % 2 == 1) return false;

        unordered_map<char, char> pairs = {
            {')', '('},
            {']', '['},
            {'}', '{'}
        };
        stack<char> stk;
        for (char ch: s) {
            if (pairs.count(ch)){
                if (stk.empty() || stk.top() != pairs[ch])
                    return false;
                stk.pop();
            }
            else
                stk.push(ch);
        }
        return stk.empty();
    }
};
```

