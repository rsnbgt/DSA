[https://leetcode.com/problems/gray-code/?envType=problem-list-v2&envId=bit-manipulation]

```cpp
class Solution {
public:
    vector<int> grayCode(int n) {
        int m=1<<n;
        vector<int> ans;
        for(int i=0;i<m;i++){
            ans.push_back(i^(i>>1));
        }
        return ans;
    }
};
```
