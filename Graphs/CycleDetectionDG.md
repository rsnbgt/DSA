## Cycle detection in directed Graph

```cpp
bool cycle(vector<vector<int>>& list,int n,vector<int>& vis){
        if(vis[n]==1) return true;
        if(vis[n]==2) return false;

        vis[n]=1;

        for(auto next:list[n]){
            if(cycle(list,next,vis)) return true;
        }
        vis[n]=2;
        return false;
    }
  ```
>Tc:O(N+E)

>SC:O(N)
