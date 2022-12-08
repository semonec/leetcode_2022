# 238. Product of Array Except Self
https://leetcode.com/problems/product-of-array-except-self/description/

Given an integer array nums, return an array answer such that answer[i] is equal to the product of all the elements of nums except nums[i].

The product of any prefix or suffix of nums is guaranteed to fit in a 32-bit integer.

You must write an algorithm that runs in O(n) time and without using the division operation.

 

### Example 1:
```
Input: nums = [1,2,3,4]
Output: [24,12,8,6]
```
### Example 2:
```
Input: nums = [-1,1,0,-3,3]
Output: [0,0,9,0,0]
```

## Constraints:

- `2 <= nums.length <= 105`
- `-30 <= nums[i] <= 30`
- The product of any prefix or suffix of nums is guaranteed to fit in a 32-bit integer.
 

Follow up: Can you solve the problem in O(1) extra space complexity? (The output array does not count as extra space for space complexity analysis.)

# Solution

[a, b, c, d] 라면


[ bcd, a*cd, ab*d, abc] 의 결과가 나오면 된다.
즉, 현재 인덱스의 좌측 원소들 곱 * 우측 원소들 곱 으로 처리

reducer를 이용해서 좌측 원소들의 곱을 밀어넣고
이후 우측 원소들의 곱을 가져와서 앞에서 구한 것에 곱해주면 된다.

reduce, reduceRight 두개를 이용하면 된다.

time compexity 는 O(2n), space complexity는 O(1)=> reduce 내부 temporary 변수 prev 두개
