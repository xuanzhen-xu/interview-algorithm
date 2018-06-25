561.Array Partition I

Description
> Given an array of 2n integers, your task is to group these integers into n pairs of integer, say (a1, b1), (a2, b2), ..., (an, bn) which makes sum of min(ai, bi) for all i from 1 to n as large as possible.

Note:
1. n is a positive integer, which is in the range of [1, 10000].
2. All the integers in the array will be in the range of [-10000, 10000].

Solution 1 (Using sorting)
```java
class Solution {
  public int arrayPairSum(int[] nums) {
    Arrays.sort(nums);
    int sum = 0;
    for (int i = 0; i < nums.length; i += 2) {
      sum += nums[i];
    }
    return sum;
  }
}
```

Solution 2 (Using bucket sort)
```java
class Solution {
  public int arrayPairSum(int[] nums) {
    int lim = 10000;
    int[] bucket =  new int[20001];
    for (int i = 0; i < nums.length; i++) {
      bucket[nums[i] + lim]++;
    }
    int count = 0, sum = 0;
    for (int i = -lim; i <= lim; i++) {
      sum += (bucket[i + lim] + 1 - count) / 2 * i;
      count = (bucket[i + lim] + 2 - count) % 2;
    }
    return sum;
  }
}
```
