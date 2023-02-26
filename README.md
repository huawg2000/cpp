# cpp

本文题源和学习路径来自于[代码随想录](https://programmercarl.com/)

## 数组
### 二分查找

二分查找运用的前提
  1.数组有序
  2.数组没有重复元素

**边界条件**
  1.左闭右闭，此时left==right有意义
  ```cpp
  while(left <= right)
  ```
  2.因为当前这个nums[i]必定不是target，所以在后续二分时要移动一个位置
  >     
  ```cpp
    if(nums[i] < target) {
        left = i + 1;
        i = left + (right - left) / 2;
    }
  ```
  >     
  ```cpp
    if(nums[i] > target) {
        right = i - 1; 
        i = left + (right - left) / 2;
    }
  ```

参考代码
  >
  ```cpp
    int search(vector<int>& nums, int target) {
        int i = (nums.size()-1)/2;
        int left = 0;
        int right = nums.size()-1;
        while(left <= right) { 
            if(nums[i] == target)return i; //当前数组i位置的元素已经参与比较，所以后续二分需要移位(+1/-1)
            else if(nums[i] < target) {
                left = i + 1; //在当前位置处移位
                i = left + (right - left) / 2;
            }
            else if(nums[i] > target) {
                right = i - 1; //在当前位置处移位
                i = left + (right - left) / 2;
            }
        }
        return -1;
    }
  ```

参考例题
[二分查找](https://leetcode.cn/problems/binary-search/)
[参考代码](https://github.com/huawg2000/cpp/blob/leetcode/src/704%E4%BA%8C%E5%88%86%E6%9F%A5%E6%89%BE.cpp)

[搜索插入位置](https://leetcode.cn/problems/search-insert-position/)

[在排序数组中查找元素的第一个和最后一个位置](https://leetcode.cn/problems/find-first-and-last-position-of-element-in-sorted-array/)

[x的平方根](https://leetcode.cn/problems/sqrtx/)

[有效的完全平方数](https://leetcode.cn/problems/valid-perfect-square/)