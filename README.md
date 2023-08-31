# 556.-Next-Greater-Element-III
556. Next Greater Element III Solution

class Solution {
    public int nextGreaterElement(int n) {
    char[] nums = String.valueOf(n).toCharArray();
    
    int i = nums.length - 2;
    while (i >= 0 && nums[i] >= nums[i + 1]) {
        i--;
    }
    
    if (i == -1) {
        return -1; // No greater integer with the same digits
    }
    
    int j = nums.length - 1;
    while (nums[j] <= nums[i]) {
        j--;
    }
    
    // Swap nums[i] and nums[j]
    char temp = nums[i];
    nums[i] = nums[j];
    nums[j] = temp;
    
    // Reverse the digits to the right of i
    reverse(nums, i + 1, nums.length - 1);
    
    try {
        return Integer.parseInt(new String(nums));
    } catch (NumberFormatException e) {
        return -1; // Integer overflow
    }
}

private void reverse(char[] nums, int start, int end) {
    while (start < end) {
        char temp = nums[start];
        nums[start] = nums[end];
        nums[end] = temp;
        start++;
        end--;
    }
}

}
