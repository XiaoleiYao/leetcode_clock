# 面试题 01.03. URL化
## URL化。编写一种方法，将字符串中的空格全部替换为%20。假定该字符串尾部有足够的空间存放新增字符，并且知道字符串的“真实”长度。（注：用Java实现的话，请使用字符数组实现，以便直接在数组上操作。）

### 示例 1：

输入："Mr John Smith    ", 13
输出："Mr%20John%20Smith"

### 示例 2：
输入："               ", 5
输出："%20%20%20%20%20"
 
### 提示：
字符串长度在 [0, 500000] 范围内。


```c++
class Solution {
public:
    string replaceSpaces(string S, int length) {
        int cnt = 0;
        for(int i = 0;i < length;++i)
        {
            if(S[i] == ' ')
            {
                ++cnt;
            }
        }
        int newLen = length + cnt * 2;
        for(int i = length - 1,j = newLen - 1;i >= 0 && i != j;--i,--j)
        {
            if(S[i] == ' ')
            {
                S[j] = '0';
                S[--j] = '2';
                S[--j] = '%';
            }
            else
            {
                S[j] = S[i];
            }
        }
        S[newLen] = '\0';
        return S;
    }
};
```

# 1528. 重新排列字符串
## 给你一个字符串 s 和一个 长度相同 的整数数组 indices 。请你重新排列字符串 s ，其中第 i 个字符需要移动到 indices[i] 指示的位置。返回重新排列后的字符串。

![image](https://user-images.githubusercontent.com/60544624/110429132-6c6ed100-80e5-11eb-9bd4-31ee64876e48.png)

输入：s = "codeleet", indices = [4,5,6,7,0,2,1,3]
输出："leetcode"
解释：如图所示，"codeleet" 重新排列后变为 "leetcode" 。


```c++
class Solution {
public:
    string restoreString(string s, vector<int>& indices) {
        std::map<int,char> m;
        for(int i = 0;i < indices.size();++i)
        {
            m[indices[i]] = s[i];
        }
        string res;
        for(auto &v : m)
        {
            res.push_back(v.second);
        }
        return res;
    }
};
```
