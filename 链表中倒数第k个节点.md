### 题目要求
输入一个链表，输出该链表中倒数第k个结点
### 思路
>第一种解法很简单，不再赘述。<br>
第二种解法：设置两个指针,一个快指针，一个慢指针。快指针先向前遍历k-1步，慢指针再从头往后走，相遇的地方就是倒数第k个节点。
### 代码
- 第一种方法
时间复杂度O(n^2)
代码如下
```c++
/*
struct ListNode {
	int val;
	struct ListNode *next;
	ListNode(int x) :
			val(x), next(NULL) {
	}
};*/
class Solution {
public:
    ListNode* FindKthToTail(ListNode* pListHead, unsigned int k) {
        if(pListHead == nullptr || k == 0) return nullptr;
        ListNode* pnode = pListHead;
        int n = 0;
        while(pnode != nullptr){
            pnode = pnode->next;
            n++;
        }
        ListNode* node = pListHead;
        if(k > n) return nullptr;
        for(int i = 0;i<n-k;i++)
                node = node->next;
        return node;
    }
};
```
- 第二种方法
只遍历一次链表
时间复杂度为O(n)
```c++
/*
struct ListNode {
	int val;
	struct ListNode *next;
	ListNode(int x) :
			val(x), next(NULL) {
	}
};*/
class Solution {
public:
    ListNode* FindKthToTail(ListNode* pListHead, unsigned int k) {
        if(pListHead == nullptr || k <= 0) return nullptr;
        ListNode* fast = pListHead;
        ListNode* low = pListHead;
        for(int i=0;i<k-1;i++){
            if(fast->next != nullptr){
                fast = fast->next;
            }else{
                return nullptr;
            }
        }
        while(fast->next != nullptr){
            fast = fast->next;
            low = low->next;
        }
        return low;
    }
};