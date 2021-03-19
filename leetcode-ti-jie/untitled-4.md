# 11. Container With Most Water

Given n non-negative integers a1, a2, ..., an , where each represents a point at coordinate \(i, ai\). n vertical lines are drawn such that the two endpoints of the line i is at \(i, ai\) and \(i, 0\). Find two lines, which, together with the x-axis forms a container, such that the container contains the most water.

Notice that you may not slant the container.

Example 1:



Input: height = \[1,8,6,2,5,4,8,3,7\] Output: 49 

Explanation: The above vertical lines are represented by array \[1,8,6,2,5,4,8,3,7\]. 

In this case, the max area of water \(blue section\) the container can contain is 49.

![](../.gitbook/assets/tu-pian-%20%2811%29.png)

Example 2:

Input: height = \[1,1\] Output: 1

Example 3:

Input: height = \[4,3,2,1,4\] Output: 16

Example 4:

Input: height = \[1,2,1\] Output: 2

Constraints:

```text
n == height.length
2 <= n <= 3 * 104
0 <= height[i] <= 3 * 104
```

题解：

```text
class Solution{
    public int maxArea(int[] height) {
        int l = 0,r = height.length - 1;
        int ans = 0;
        while(l<r) { 
            int area = Math.min(height[r],height[l])*(r - l);
            ans = Math.max(ans,area);
            if(height[l]<=height[r]){
            l++;
            }
            else{
                r--;
            }
        } 
        return ans;
    }
}
```

這個思想類似於第一題，我們對每一次求面積做一次記錄，找出最大的。左指針和右指針分別位於數組的最左和最右以便查，然後對兩者的長度做一次比較，較小的往裡面走，簡單來說就是l++，r---。事實上，我們並不能確定什麼時候最大，所以數組要循環一遍來進行查找。 （可能第一個就找到了最大值，但這種情況我們並不能進行判斷。

