Roman to Integer:
Approach：
By traversing the Roman numeral string from right to left, we can directly determine if the next (i.e., left) digit is smaller than the previous (i.e., right) one, eliminating unnecessary nested if statements.
The core logic is as follows:Use a temporary variable last to store the value of the previously read character. If the current character’s value is smaller than last, it indicates a special combination (e.g., IV=4, IX=9); otherwise, we simply add the current value to the total sum.

(罗马数字转整数：

思路：

从后向前查找，可以直接判断下一位是否比上一位大，减少不必要的嵌套if。

大体思路就是：用一个临时变量last表示上一个读取的值，如果比下一位大，就是特殊判断。否则就是正常加。）



Example:For the input "IV":
The program first reads "V" (the rightmost character), which maps to 5. Since 5 > 0 (initial value of last), the condition current value < last is not met.
At this point: sum = 0 + 5; last = 5;
Next, the program reads "I", which maps to 1. Since 1 < 5 (last), the condition is met, so we subtract 1 from the sum.
At this point: sum = 5 - 1; last = 1;



（举个例子：

"IV"：    程序开始，s[i]读取到了“V”，对应的case = 5 > 0, 所以5 < last的判断不成立。

​                此时：sum = 0 + 5; last = 5;

​                然后s[i]读取到了"I",1 < 5(last),判断成立，所以减去1。

​                此时：sum = 5 - 1;last = 1;）



Implementation Process

> Initially, I used a brute-force approach with numerous nested if statements. Later, I switched to a hash map for value mapping, but neither approach achieved 100% efficiency. Ultimately, I implemented the logic with a switch statement for optimal performance.





解题过程

> 一开始暴力疯狂if，后面改成映射，发现效率都没到100%。所以用Switch来写。



Complexity Analysis

- Time Complexity: O(n)
- Space Complexity: O(1)



（复杂度

- 时间复杂度: O(n)

- 空间复杂度: O(1)

  ）

```cpp
class Solution {
public:
    int romanToInt(string s) {
        int sum = 0;
        int last = 0;
        for (int i = s.size() - 1; i >= 0; --i) {
            switch(s[i]) {
                case 'M': 
                    if (1000 < last) sum -= 1000;
                    else sum += 1000;
                    last = 1000;
                    break;
                case 'D': 
                    if (500 < last) sum -= 500;
                    else sum += 500;
                    last = 500;
                    break;
                case 'C': 
                    if (100 < last) sum -= 100;
                    else sum += 100;
                    last = 100;
                    break;
                case 'L': 
                    if (50 < last) sum -= 50;
                    else sum += 50;
                    last = 50;
                    break;
                case 'X': 
                    if (10 < last) sum -= 10;
                    else sum += 10;
                    last = 10;
                    break;
                case 'V': 
                    if (5 < last) sum -= 5;
                    else sum += 5;
                    last = 5;
                    break;
                case 'I': 
                    if (1 < last) sum -= 1;
                    else sum += 1;
                    last = 1;
                    break;
                default: 
                    last = 0;
                    break;
            }
        }
        return sum;
    }
};
```