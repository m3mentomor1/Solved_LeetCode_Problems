# 9. Palindrome Number


### Problem:
Given an integer  ``x``, return true if ``x`` is a palindrome, and ``false`` otherwise.


Example 1:
> Input: x = 121

> Output: true

> Explanation: 121 reads as 121 from left to right and from right to left.

Example 2:
> Input: x = -121

> Output: false

> Explanation: From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome.

Example 3:
> Input: x = 10

> Output: false

> Explanation: Reads 01 from right to left. Therefore it is not a palindrome.
 

Constraints:

``-2^(31) <= x <= 2^(31) - 1``
 

Follow up: Could you solve it without converting the integer to a string?




### Solution:

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

