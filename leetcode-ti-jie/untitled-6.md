# 9. Palindrome Number

Given an integer x, return true if x is palindrome integer.

An integer is a palindrome when it reads the same backward as forward. For example, 121 is palindrome while 123 is not.

Example 1:

Input: x = 121 Output: true

Example 2:

Input: x = -121 Output: false Explanation: From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome.

Example 3:

Input: x = 10 Output: false Explanation: Reads 01 from right to left. Therefore it is not a palindrome.

Example 4:

Input: x = -101 Output: false

Constraints:

```text
-231 <= x <= 231 - 1
```

题解：

```text
class Solution{
    public boolean isPalindrome(int x){
        int y = x;
        if(x == 0)return true;
        if(x < 0 )return false;
        int reversed = 0;
        while(y>0){
            reversed = reversed * 10 + y % 10;
            y /= 10;
        }
        return x == reversed;
    }
}
```

對於此題有兩種思路，第一個是切一半看，第二個是全部轉換，我覺得第二個思路更加清晰。

 先讓y記錄x的值，然後對x判斷，0一定滿足條件。小於0一定錯，於是我們就進行一個回文數變換，得到這個數如果和原來的數相等，就可以認為是回文數。

