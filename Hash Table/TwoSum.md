## 1. Two Sum -- 简单
<blockquote>
Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.
You may assume that each input would have exactly one solution, and you may not use the same element twice.
You can return the answer in any order.

Example 1:
Input: nums = [2,7,11,15], target = 9, Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
Example 2:
Input: nums = [3,2,4], target = 6, Output: [1,2]
Example 3:
Input: nums = [3,3], target = 6, Output: [0,1]
</blockquote>

<blockquote>
思路：
第一种方法 - brute force 暴力破解
把每一个数列中的数字两两相加，找出和为target的一对数字  
Time Complexity为O(n^2)  
Space Complexity为O(1)  

第二种方法 - hash table哈希表
用哈希表来存第一个数字所需要的第二个数字，在第二个数字出现时返回两个数字的index  
Time Complexity为O(n)  
Space Complexity为O(n)  
</blockquote>

<pre>
    function twoSum(nums, target) {
        //创造一个空的哈希表
        let ht = {};
        for (num of nums) {
            if (num in ht) {
                // num是ht的一个key，找到了pair中的第二个数字
                // 第一个数字的index为ht[num]
                // 第二个数字的index为nums.indexOf(num)
                return [ht[num], nums.indexOf(num)];
            } else {
                //num不是哈希表的key，把它加入哈希表看之后能不能找到他的pair
                //设哈希表的key为第一个数字的pair，value为第一个数字的index
                ht[target - num] = nums.indexOf(num);
            }
        }
    }
</pre>