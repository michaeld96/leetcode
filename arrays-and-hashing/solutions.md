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

## Valid Anagram
```cpp
class Solution {
public:
    bool isAnagram(string s, string t) {
        // First, check if the strings are the same length.
        if (s.size() != t.size())
        {
            return false;
        }
        std::unordered_map hash_1 = count_letters_in_string(s);
        std::unordered_map hash_2 = count_letters_in_string(t);
        for (int i = 0; i < s.size(); ++i)
        {
            auto itr1 = hash_1.find(s[i]);
            auto itr2 = hash_2.find(s[i]);
            if (itr1 == hash_1.end() || itr2 == hash_2.end()) { return false; }
            if (itr1->first != itr2->first ||
                itr1->second != itr2->second)
            {
                return false;
            }
        }
        return true;
    }
    std::unordered_map<char, int> count_letters_in_string(string word)
    {
        std::unordered_map<char, int> hash;
        for (int i = 0; i < word.size(); ++i)
        {
            // Not found, add into container.
            if (hash.find(word[i]) == hash.end())
            {
                hash.insert({word[i], 1});
            }
            else
            {
                auto itr = hash.find(word[i]);
                itr->second++;
            }
        }
        return hash;
    }
};
```

## Two Sum 

```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        std::unordered_map<int, int> hash;
        for (int i = 0; i < nums.size(); ++i)
        {
            int complement = target - nums[i];
            if (hash.find(complement) != hash.end())
            {
                return {hash[complement], i};
            }
            else
            {
                hash.insert({nums[i], i});
            }
        }
        return{0, 0};
    }
};
```