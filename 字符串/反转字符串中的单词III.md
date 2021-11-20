## 反转字符串中的单词III

**简单**

题目：给定一个字符串，你需要反转字符串中每个单词的字符顺序，同时仍保留空格和单词的初始顺序。

示例：

```
输入："Let's take LeetCode contest"
输出："s'teL ekat edoCteeL tsetnoc"
```

题解：

```javascript
/**
 * @param {string} s
 * @return {string}
 */
var reverseWords = function(s) {
    function reverse(strArr, left, right) {
        while(left < right) {
            const temp = strArr[left];
            strArr[left] = strArr[right];
            strArr[right] = temp;
            left++; right--;
        }
        return strArr.join("")
    }

    let strArr = s.split(" ");
    let res = ""
    for(let i=0; i<strArr.length; i++) {
        const str = i==strArr.length - 1 ? "" : " "
        res = res + reverse(strArr[i].split(""), 0,  strArr[i].length - 1) + str
    }
    return res
};
```

**思路**：通过split(" ")来分割字符串得到单词数组，再分割每个单词得到单字符数组，通过双指针反转单字符数组，再依次拼接