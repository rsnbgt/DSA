Approach 1:
``` cpp
class Solution {
public:
    vector<vector<int>> ans;
    void helper(int n,unordered_map<int,int>& mp,vector<int>temp){
        if(temp.size()==n){
            ans.push_back(temp);
            return;
        }
        for(auto & [val,freq]:mp){
            if(freq==0) continue;
            temp.push_back(val);
            mp[val]--;
            helper(n,mp,temp);
            temp.pop_back();
            mp[val]++;
        }
    }
    vector<vector<int>> permuteUnique(vector<int>& nums) {
        unordered_map<int,int> mp;
        for(int num:nums) mp[num]++;
        helper(nums.size(),mp,{});
        return ans;
    }
};
```

Approach 2 for permuataions:
```cpp
class Solution {
public:
    void helper(vector<int>& nums,vector<vector<int>>& ans,int n,int index){
        if(index==n){
            ans.push_back(nums);
            return;
        }

        for(int i=index;i<n;i++){
            swap(nums[i],nums[index]);
            helper(nums,ans,n,index+1);
            swap(nums[i],nums[index]);
        }
    }
    vector<vector<int>> permute(vector<int>& nums) {
        vector<vector<int>> ans;
        helper(nums,ans,nums.size(),0);
        return ans;
    }
};
```
> tc:n.n!

>sc:n
