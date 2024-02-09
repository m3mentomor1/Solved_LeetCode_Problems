# 933. Number of Recent Calls

## Problem:
You have a ``RecentCounter`` class which counts the number of recent requests within a certain time frame.

Implement the ``RecentCounter`` class:

``RecentCounter()`` Initializes the counter with zero recent requests.
``int ping(int t)`` Adds a new request at time ``t``, where ``t`` represents some time in milliseconds, and returns the number of requests that has happened in the past ``3000`` milliseconds (including the new request). Specifically, return the number of requests that have happened in the inclusive range ``[t - 3000, t]``.
It is guaranteed that every call to ping uses a strictly larger value of t than the previous call.

Example 1:

Input
["RecentCounter", "ping", "ping", "ping", "ping"]
[[], [1], [100], [3001], [3002]]
Output
[null, 1, 2, 3, 3]

Explanation
RecentCounter recentCounter = new RecentCounter();
recentCounter.ping(1);     // requests = [1], range is [-2999,1], return 1
recentCounter.ping(100);   // requests = [1, 100], range is [-2900,100], return 2
recentCounter.ping(3001);  // requests = [1, 100, 3001], range is [1,3001], return 3
recentCounter.ping(3002);  // requests = [1, 100, 3001, 3002], range is [2,3002], return 3
 

Constraints:

1 <= t <= 109
Each test case will call ping with strictly increasing values of t.
At most 104 calls will be made to ping.

## Solution:
```
class Solution(object):
    def isPalindrome(self, x):
        """
        :type x: int
        :rtype: bool
        """
        # Special cases:
        # If x is negative or ends with 0 & not 0 itself, it's not a palindrome
        if x < 0 or (x % 10 == 0 and x != 0):
            return False
        
        reversed_num = 0
        original_x = x
        
        # Reverse half of the number
        while x > reversed_num:
            reversed_num = reversed_num * 10 + x % 10
            x //= 10
        
        # If the number of digits in x is odd, we need to divide reversed_num by 10
        # to eliminate the middle digit
        return x == reversed_num or x == reversed_num // 10

# Test cases
solution = Solution()
print(solution.isPalindrome(121))  # Output: true
print(solution.isPalindrome(-121)) # Output: false
print(solution.isPalindrome(10))   # Output: false

```

