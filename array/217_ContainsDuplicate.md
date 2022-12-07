# 217. Contains Duplicate
URL: https://leetcode.com/problems/contains-duplicate/description/

Given an integer array nums, return true if any value appears at least twice in the array, and return false if every element is distinct.


## Example 1:

```
Input: nums = [1,2,3,1]
Output: true
```

## Example 2:

```
Input: nums = [1,2,3,4]
Output: false
```

### Example 3:

```
Input: nums = [1,1,1,3,3,4,3,2,4,2]
Output: true
```

## Constraints:

`1 <= nums.length <= 105`
`-109 <= nums[i] <= 109`


# Answer

```
var containsDuplicate = function(nums) {
    const map = new Set()
    for (let i = 0; i < nums.length; i++) {
        if (map.has(nums[i])) {
            return true
        }
        map.add(nums[i]) 
    }
    return false

};
```

## Description

array 내부 element의 중복 여부를 찾는 문제,

## 키워드

- 중복
- array

set을 만들고 array를 iteration 하면서 값을 하나씩 set에 넣는다.
값이 있다면 return true로 마무리.
다 돌때까지 값이 없다면 return false로 마무리

**Time Complexity** : O(n) => array iteration for loop 1time
**Space Complexity**: O(n) => 최대 Array size -1만큼 Set이 늘어나니깐 set의 크기만큼 O(n-1) = O(n)
