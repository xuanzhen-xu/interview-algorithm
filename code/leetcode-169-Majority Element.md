169.Majority Element

Description
> Given an array of size n, find the majority element. The majority element is the element that appears more than ⌊ n/2 ⌋ times. You may assume that the array is non-empty and the majority element always exist in the array.


Solution 1 (Sorting)
```java
class Solution {
  public int majorityElement(int[] nums) {
    Arrays.sort(nums);
    return nums[nums.length / 2];
  }
}
```

Solution 2 (HashMap)
```java
class Solution {
  public int majorityElement(int[] nums) {
    Map<Integer, Integer> map =  new HashMap<>();
    int maxCount = 0, major = nums[0];
    for (int num : nums) {
      int count = map.getOrDefault(num, 0) + 1;
      map.put(num, count);
      if (count > maxCount) {
        maxCount = count;
        major = num;
      }
    }
    return major;
  }
}
```

Solution 3 (Voting)
```java
class Solution {
  public int majorityElement(int[] nums) {
    int major = nums[0], count = 0;
    for (int num : nums) {
      if (num == major) {
        count++;
      } else if (count-- == 0) {
        major = num;
        count = 1
      }
    }
    return major;
  }
}
```
