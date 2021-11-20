## 两个数组的交集II

**简单**

题目：给定两个数组，编写一个函数来计算它们的交集。

示例：

```
输入：nums1 = [1,2,2,1], nums2 = [2,2]
输出：[2,2]
```

题解：

```javascript
/**
 * @param {number[]} nums1
 * @param {number[]} nums2
 * @return {number[]}
 */
var intersect = function(nums1, nums2) {
    let hash = {}, res = [];
    
    for(let i=0; i<nums1.length; i++) {
        if(hash[nums1[i]]) {
            hash[nums1[i]]++;
        } else {
            hash[nums1[i]] = 1;
        }
    }

    for(let j=0; j<nums2.length; j++) {
        if(hash[nums2[j]] && hash[nums2[j]] > 0) {
            res.push(nums2[j]);
            hash[nums2[j]]--;
        }
    }
    return res;
};
```

**思路**：利用js对象哈希表结构，存储nums1数组为key值，value值为出现的个数，在nums2根据哈希来寻找。
