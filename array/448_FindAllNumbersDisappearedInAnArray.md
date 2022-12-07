Given an array `nums` of n integers where `nums[i]` is in the range `[1, n]`, return an array of all the integers in the range `[1, n]` that do not appear in `nums`.

 

### Example 1:

```
Input: nums = [4,3,2,7,8,2,3,1]
Output: [5,6]
```

### Example 2:

```
Input: nums = [1,1]
Output: [2]
```

## Constraints:

- `n == nums.length`
- `1 <= n <= 105`
- `1 <= nums[i] <= n`
 

**Follow up**: Could you do it without extra space and in O(n) runtime? You may assume the returned list does not count as extra space.

# Solution

```
var findDisappearedNumbers = function(nums) {
    for (let i = 0; i < nums.length; i++) {
        const index = Math.abs(nums[i]) -1
        if (nums[index] > 0) nums[index] *= -1
    }
    const result = []
    for (let i = 0; i < nums.length; i++) {
        if (nums[i] > 0) result.push(i+1)
    }
    return result
};
```

### keyword
- without Extra space (in-place 치환)
- O(n) runtime => iteration

n이 1이상의 자연수이므로, nums[i] 의 값에 해당하는 element의 값을 음수로 변경해주면, 처음부터 돌면서 해당 position 이 양수인 것들의 position값을 result에 담아준다.
