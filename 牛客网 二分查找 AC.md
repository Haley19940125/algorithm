### 题目要求
给定一个有序整数数组A及它的大小n，同时给定要查找的元素val，请返回它在数组中的位置(从0开始)，若不存在该元素，返回-1。若该元素出现多次，请返回第一次出现的位置。
### Example
测试样例：
[1,3,5,7,9],5,3
返回：1
### 思路
给定了一个有序的数组，考虑用二分查找法。时间复杂度：O（logn），比较简单
### 代码
```c++
class BinarySearch {
public:
    int getPos(vector<int> A, int n, int val) {
        // write code here
        int i = 0;
        int j = n-1;
        while(i<=j){
            int middle = (i+j)/2;
            if(val == A[middle]){
                while(val == A[middle]){
                    middle--;
                }
                return middle+1;
            }
            if(val > A[middle]){
                i = middle +1;
            }
            if(val < A[middle]){
                j = middle -1;
            }
        }
        return -1;
    }
};