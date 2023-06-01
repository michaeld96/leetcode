## Contains Duplicate

```cpp
class Solution {
public:
    bool containsDuplicate(vector<int>& nums) {
        unordered_map<int, string> bucket;
        for (size_t i = 0; i < nums.size(); ++i)
        {   
            if (bucket.find(nums[i]) == bucket.end())
            {
                bucket.insert(make_pair(nums[i] ,""));
            }
            else
            {
                return true;
            }
        }
        return false;
    }
};
```