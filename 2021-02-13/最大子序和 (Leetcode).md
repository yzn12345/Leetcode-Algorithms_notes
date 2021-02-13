```Java
class Solution {
    public int maxSubArray(int[] nums) {
        if (nums.length == 1) {
            return nums[0];
        }
        
        int[] dp = new int[nums.length];
        dp[0] = nums[0];
        int max = nums[0];
        for (int i = 1; i < nums.length; i++) {
            dp[i] = Math.max(dp[i-1] + nums[i], nums[i]);
            max = Math.max(dp[i], max);
        }
        return max;
    }
}
```

dp属实难理解
思路：一个dp表，每个index取遍历到当前元素可以得到的最大continuous subarry。选择一：如果dp[i-1] > 0， 那么当前最大可能性就是dp[i-1]+自己。 选择二: 如果dp[i-1] <= 0, 自立门户，在当前index截断，新的maximum subarray目前就是自己。

