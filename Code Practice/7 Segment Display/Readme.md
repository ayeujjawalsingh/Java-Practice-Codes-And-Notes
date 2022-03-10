## 7 Segment Display
Using seven segment display, you can write down any digit from 0 to 9 using at most seven segments. Given a positive number N and then a string S representing a number of N digits. You have to rearrange the segments in this N digit number to get the smallest possible N digit number. This number can have leading zeros. You can not waste any segment or add any segment from your own. You have to use all of the segments of the given N digits.

Note: You can refer this diagram for more details

[🔗Goto](https://practice.geeksforgeeks.org/problems/7-segment-display0752/1#) 

```
Example 1:

Input:
N = 6
S = "234567"
Output:
000011
Explanation:
234567 has a total of 28 segments and
we can rearrange them to form 000011
which has 28 segments too. 000011 is the
smallest possible number which can be
formed on rearrangement.

Example 2:

Input:
N = 3
S = "011"
Output:
011
Explanation:
011 has a total of 10 segments and this
is the smallest number with 10 segments.
```
<details>
<summary>Full Code</summary>

```java

```
</details>

```java
class Solution
{
    static String sevenSegments(String S, int N)
    {
        // code here
        int segments[] = {6, 2, 5, 5, 4, 5, 6, 3, 7, 5};
        
        int total_segments = 0;
        for(int i=0; i<N; i++)
        {
            int ch = S.charAt(i)-'0';
            total_segments += segments[ch];
        }
        
        int a[] = new int[N];
        
        for(int i=0; i<N; i++)
        {
            a[i] = 2;
            total_segments-=2;
        }
        
        HashMap<Integer, Integer> map = new HashMap<>();
        
        map.put(6, 0);
        map.put(2, 1);
        map.put(5, 2);
        map.put(4, 4);
        map.put(3, 7);
        map.put(7, 8);
        
        
        int i = 0;
        
        while(total_segments>=4 && i<N)
        {
            a[i++] += 4;
            total_segments -= 4;
        }
        
        int j = N-1;
        
        while(total_segments>0 && j>=0)
        {
            int res = 7-a[j];
            int min_val = Math.min(total_segments, res);
            a[j] += min_val;
            total_segments -= min_val;
            j--;
        }
        
        StringBuilder ans = new StringBuilder();
        
        for(int x : a)
        {
            ans.append(map.get(x));
        }
        
        
        return ans.toString();
        
        
    }
};
```
