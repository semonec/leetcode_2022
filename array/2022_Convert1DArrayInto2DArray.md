# 2022. Convert 1D Array Into 2D Array

You are given a **0-indexed** 1-dimensional (1D) integer array `original`, and two integers, `m` and `n`. You are tasked with creating a 2-dimensional (2D) array with  m rows and n columns using all the elements from original.

The elements from indices 0 to n - 1 (inclusive) of original should form the first row of the constructed 2D array, the elements from indices n to 2 * n - 1 (inclusive) should form the second row of the constructed 2D array, and so on.

Return an m x n 2D array constructed according to the above procedure, or an empty 2D array if it is impossible.

 

### Example 1:

```
Input: original = [1,2,3,4], m = 2, n = 2
Output: [[1,2],[3,4]]
Explanation: The constructed 2D array should contain 2 rows and 2 columns.
The first group of n=2 elements in original, [1,2], becomes the first row in the constructed 2D array.
The second group of n=2 elements in original, [3,4], becomes the second row in the constructed 2D array.
```

### Example 2:

```
Input: original = [1,2,3], m = 1, n = 3
Output: [[1,2,3]]
Explanation: The constructed 2D array should contain 1 row and 3 columns.
Put all three elements in original into the first row of the constructed 2D array.
```

### Example 3:
```
Input: original = [1,2], m = 1, n = 1
Output: []
Explanation: There are 2 elements in original.
It is impossible to fit 2 elements in a 1x1 2D array, so return an empty 2D array.
```

## Constraints:

- `1 <= original.length <= 5 * 104`
- `1 <= original[i] <= 105`
- `1 <= m, n <= 4 * 104`

# Solution

## Keyword

- array transform
- slice and push

## Answer 1
간단한 방법
splice 후 push
근데 성능이 좀 떨어진다, m과 n이 적절하게 균형이 맞아서 square에 근접하게 된다면 time complexity가 늘어날 수 있다.
다만 space 차원에서는 효율적이다.

```
var construct2DArray = function(original, m, n) {
    // exception case
    if (original.length !== m*n) return []

    const result = []
    for (let i = 0 ; i < m ; i++) {
        result.push(original.splice(0, n))
    }

    return result
};
```

## Answer 2

조금 복잡하지만 O(n)을 보장
array iteration을 하면서 temp에 현재 시점의 값을 넣고, 시점이 n의 배수가 될때마다 result에 temp를 push하고 클리어

```
var construct2DArray = function(original, m, n) {
    // exception case
    if (original.length !== m*n) return []

    const result = []
    let temp = []
    for (let i = 0; i < original.length; i++) {
        temp.push(original[i])
        if ( (i+1) % n === 0) {
            result.push(temp)
            temp = []
        }
    }
    return result
};
```
