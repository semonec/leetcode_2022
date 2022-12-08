# 287. Find the Duplicate Number

https://leetcode.com/problems/find-the-duplicate-number/

Given an array of integers nums containing n + 1 integers where each integer is in the range [1, n] inclusive.

There is only one repeated number in nums, return this repeated number.

You must solve the problem without modifying the array nums and uses only constant extra space.

 

### Example 1:
```
Input: nums = [1,3,4,2,2]
Output: 2
```
### Example 2:
```
Input: nums = [3,1,3,4,2]
Output: 3
```

## Constraints:

- `1 <= n <= 105`
- `nums.length == n + 1`
- `1 <= nums[i] <= n`
- All the integers in nums appear only once except for precisely one integer which appears two or more times.
 

Follow up:

- How can we prove that at least one duplicate number must exist in nums?
- Can you solve the problem in linear runtime complexity?

# solution

**Keyword:**
- find duplicated
- n은 양수다

array를 순회하면서 해당 위치의 값에 해당하는 index의 값을 음수로 변환하고,
만약 현재 인덱스 value가 음수라면 해당 인덱스가 중복
```
var findDuplicate = function(nums) {
    for (let i = 0; i < nums.length; i ++) {
        const index = Math.abs(nums[i])
        if (nums[index] < 0) return index
        nums[index] = nums[index] * -1
    }
};
```
