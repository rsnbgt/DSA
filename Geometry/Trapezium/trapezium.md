
```cpp
class Solution {
public:
    int hash(int a,int b){
        return a*4003+b;
    }
    int countTrapezoids(vector<vector<int>>& points) {
        int n=points.size();
        
        unordered_map<int,unordered_map<int,int>> slope_c_map;
        unordered_map<int,unordered_map<int,map<int,int>>> slope_c_len;

        for(int i=0;i<n;i++){
            int x0=points[i][0],y0=points[i][1];
            for(int j=i+1;j<n;j++){
                int x1=points[j][0],y1=points[j][1];
                int b=x0-x1,a=y1-y0;
                int length=a*a+b*b;
                
                if(a==0){
                    b=1;
                }else if(b==0){
                    a=1;
                }else{
                    int gcd=__gcd(abs(a),abs(b));
                    a/=gcd,b/=gcd;
                    if(a<0){
                        a=-a,b=-b;
                    }
                }
                int c=a*x0+b*y0;

                slope_c_map[hash(a,b)][c]++;
                slope_c_len[hash(a,b)][c][length]++;
            }
        }
        int total=0;
        for(auto &[slopes,counts]:slope_c_map){
            int sum=0;
            for(auto& [c,count]:counts){
                total+=count*sum;
                sum+=count;
            }
        }
        int llgrams=0;
        for(auto& [slopes,counts]:slope_c_len){
            map<int,int> prev;
            for(auto &[c,count_length]:counts){
                for(auto & [len,count]:count_length){
                    llgrams+=count*prev[len];
                    prev[len]+=count;
                }
            }
        }
        return total-llgrams/2;
    }
};
```
