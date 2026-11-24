# 3411. Maximum Subarray With Equal Products

**Difficulty:** Easy
**Link:** https://leetcode.com/problems/maximum-subarray-with-equal-products/

## Problem

You are given an array of positive integers `nums`.

An array `arr` is called product equivalent if `prod(arr) == lcm(arr) * gcd(arr)`, where:

- `prod(arr)` is the product of all elements of `arr`.
- `gcd(arr)` is the GCD of all elements of `arr`.
- `lcm(arr)` is the LCM of all elements of `arr`.

Return the length of the longest product equivalent subarray of `nums`.

### Example 1

```
Input: nums = [1,2,1,2,1,1,1]
Output: 5
Explanation:
The longest product equivalent subarray is [1, 2, 1, 1, 1], where
prod([1, 2, 1, 1, 1]) = 2, gcd([1, 2, 1, 1, 1]) = 1, and lcm([1, 2, 1, 1, 1]) = 2.
```

### Example 2

```
Input: nums = [2,3,4,5,6]
Output: 3
Explanation:
The longest product equivalent subarray is [3, 4, 5].
```

### Example 3

```
Input: nums = [1,2,3,1,4,5,1]
Output: 5
```

### Constraints

- `2 <= nums.length <= 100`
- `1 <= nums[i] <= 10`

## Approach

Brute force over every subarray, extended one element at a time.

- For each start index `i`, extend the end index `j` and keep a running product, LCM and GCD.
- A subarray is product equivalent when `prod == lcm * gcd`, so update the answer whenever that holds.
- Prune: the product can never be less than `lcm * gcd` for these values, and `lcm * gcd` is bounded by `10! * 10 = 36,288,000`. Once the product exceeds that bound, no longer subarray from this start can match, so break. This also keeps the product from overflowing `int`.

**Time:** O(n² · log M), where `M` is the maximum element
**Space:** O(1)

## Solution

See [`Solution.java`](./Solution.java).
