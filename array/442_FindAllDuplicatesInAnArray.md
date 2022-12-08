# 442. Find All Duplicates in an Array

https://leetcode.com/problems/find-all-duplicates-in-an-array/

Given an integer array nums of length n where all the integers of nums are in the range [1, n] and each integer appears once or twice, return an array of all the integers that appears twice.

You must write an algorithm that runs in O(n) time and uses only constant extra space.

 

### Example 1:
```
Input: nums = [4,3,2,7,8,2,3,1]
Output: [2,3]
```
### Example 2:
```
Input: nums = [1,1,2]
Output: [1]
```
### Example 3:
```
Input: nums = [1]
Output: []
``` 

## Constraints:

- `n == nums.length`
- `1 <= n <= 105`
- `1 <= nums[i] <= n`
- Each element in nums appears once or twice.

# solution

**keyword:**
- find duplicated
- number 는 양수

다른 duplicated 찾는것처럼 인덱스 위치의 값을 음수로 변환하고 현재 인덱스의 값이 음수라면 result array에 push 아니라면 현재 인덱스의 값을 음수로 변경
```
var findDuplicates = function(nums) {
    const result = []

    for (let i = 0; i < nums.length; i++) {
        const index = Math.abs(nums[i]) -1
        if (nums[index] < 0)
            result.push(index + 1)
        else
            nums[index] *= -1
    }
    return result
};
```
