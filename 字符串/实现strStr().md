## 实现strStr()

**简单**

题目：给你两个字符串 haystack 和 needle ，请你在 haystack 字符串中找出 needle 字符串出现的第一个位置（下标从 0 开始）。如果不存在，则返回  -1 。

示例：

```
输入：haystack = "hello", needle = "ll"
输出：2
```

题解：

```javascript
/**
 * @param {string} haystack
 * @param {string} needle
 * @return {number}
 */
var strStr = function(haystack, needle) {
    if(needle === "") return 0;
    let m = haystack.length, n = needle.length;
    level1:for(let i=0; i<=m-n; i++) {
        let j;
        level2:for(j=0; j<n; j++) {
            if(haystack[i+j] !== needle[j]) break level2;
        }
        if(j === n) return i;
    }
    return -1;
};
```

