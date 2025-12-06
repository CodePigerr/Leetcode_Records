Merging two sorted linked lists:

 First off, I just merged the two lists and then did a bubble sort on the result. Weirdly enough, it still ended up with 100% space complexity – and it’s definitely O(N²) time complexity to boot. 

The official solution though? Recursive approach with O(N) time. So I’m just jotting down the official one here. My janky "merge-then-sort" code was a total eyesore and miles long lmao.

(合并两个有序链表:

最开始先合并两个链表，然后冒泡排序，结果莫名其妙也是100%空间复杂度，不过应该是O(N²)。

然后官方题解是递归O(N).这里就记录官方题解了，我写的合并加排序代码又臭又长哈哈哈。

)

```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* mergeTwoLists(ListNode* list1, ListNode* list2) {
        if(list1 == NULL)
        return list2;
    if(list2 == NULL)
        return list1;
    if(list1->val < list2->val){
        list1->next = mergeTwoLists(list1->next, list2);
        return list1;
    }else{
        list2->next = mergeTwoLists(list1, list2->next);
        return list2;
    }}
};
```

