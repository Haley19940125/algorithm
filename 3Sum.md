### 题目要求
Given an array S of n integers, are there elements a, b, c in S such that a + b + c = 0? Find all unique triplets in the array which gives the sum of zero.

Note: The solution set must not contain duplicate triplets.
### example
For example, given array S = [-1, 0, 1, 2, -1, -4],

A solution set is:
[
  [-1, 0, 1],
  [-1, -1, 2]
]
### 思路
- 解法
> 将数组排序，此时的数组从小到大排序。从第一位【i】开始遍历，设置两个指针，一个指向当前位置的后一位【low】，一个指向最后数组最后一位【high】。然后判断三个的和【sum】，如果大于0，则说明【high】位需要往前移一位；如果小于0，则说明【low】的位置需要往后移一位；如果等于0，则说明符合题目，将这三个数值存在数组向量中。
- 需要考虑的问题
> 去重。重复的结果不要显示。
用while循环判断重复，如果重复的话就往后移。
### 代码
```c++
/**
时间复杂度为O(n^2)
**/
class Solution {
public:
    vector<vector<int>> threeSum(vector<int>& nums) {
        vector <vector<int>> res;
        sort(nums.begin(),nums.end());
        int size = nums.size();
        for(int i=0;i<size;i++){
            int low = i+1;
            int high = size - 1;
            while(low <high){
                int sum = nums[low] + nums[high];
                if(sum + nums[i] < 0){
                    low++;
                }else if(sum + nums[i] > 0){
                    high--;
                }else{
                    vector<int> storage(3,0);
                    storage[0] = nums[i];
                    storage[1] = nums[low];
                    storage[2] = nums[high];
                    while(low<high && nums[low] == storage[1]) low++;
                    while(low<high && nums[high] == storage[2]) high--;
                    res.push_back(storage);
                }
            }
            while(i<size-1 && nums[i+1] == nums[i]) i++;
        }
        return res;
    }
};
```