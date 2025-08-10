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
