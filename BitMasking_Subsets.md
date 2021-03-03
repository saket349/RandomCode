## Bit Masking

### Given an integer array nums of unique elements, return all possible subsets (the power set).
### The solution set must not contain duplicate subsets. Return the solution in any order.

```
vector<vector<int>> subsets(vector<int>& nums) {
        int size = nums.size();
        int subsetnum = (1<<size);
        vector<vector<int> > allsubsets;
        for(int subsetmask = 0;subsetmask < subsetnum;subsetmask++){
            vector<int> subset;
            for(int i=0;i<size;i++){
                if((subsetmask&(1<<i))!=0){
                    subset.push_back(nums[i]);
                }
            }
            allsubsets.push_back(subset);
        }
        return allsubsets;
    }

```
