## Maximum average subarray
Given an array Arr of size N and a positive integer K, find the sub-array of length K with the maximum average. [🔗Goto](https://practice.geeksforgeeks.org/problems/maximum-average-subarray5859/1#) 

```
Example 1:

Input:
K = 4, N = 6
Arr[] = {1, 12, -5, -6, 50, 3}
Output: 12 -5 -6 50
Explanation: Maximum average is 
(12 - 5 - 6 + 50)/4 = 51/4.

Example 2:

Input:
K = 3, N = 7
Arr[] = {3, -435, 335, 10, -50, 100, 20}
Output: 335 10 -50
Explanation: Maximum average is 
(335 + 10 - 50)/3 = 295/3.
```
<details>
<summary>Full Code</summary>

```java
import java.io.*;
import java.util.*;

public class GFG {
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int tc = Integer.parseInt(br.readLine().trim());
        while (tc-- > 0) {
            String[] inputLine;
            inputLine = br.readLine().trim().split(" ");
            int k = Integer.parseInt(inputLine[0]);
            inputLine = br.readLine().trim().split(" ");
            int n = Integer.parseInt(inputLine[0]);
            int[] arr = new int[n];
            inputLine = br.readLine().trim().split(" ");
            for (int i = 0; i < n; i++) {
                arr[i] = Integer.parseInt(inputLine[i]);
            }

            int ans = new Solution().findMaxAverage(arr, n, k);
            for(int i=ans; i<ans+k; i++)
                System.out.print(arr[i]+" ");
            System.out.println();
        }
    }
}
// } Driver Code Ends


//User function Template for Java

class Solution {
    int findMaxAverage(int[] arr, int n, int k) {
         if (k > n) return -1;

        // Compute sum of first 'k' elements
        int sum = arr[0];
        for (int i = 1; i < k; i++) 
            sum += arr[i];

        int max_sum = sum, max_end = k - 1;

        // Compute sum of remaining subarrays
        for (int i = k; i < n; i++) {
            sum = sum + arr[i] - arr[i - k];
            if (sum > max_sum) {
                max_sum = sum;
                max_end = i;
            }
        }
        // Return starting index
        return max_end - k + 1;
    }
}

```
</details>

```java
class Solution {
    int findMaxAverage(int[] arr, int n, int k) {
         if (k > n) return -1;

        // Compute sum of first 'k' elements
        int sum = arr[0];
        for (int i = 1; i < k; i++) 
            sum += arr[i];

        int max_sum = sum, max_end = k - 1;

        // Compute sum of remaining subarrays
        for (int i = k; i < n; i++) {
            sum = sum + arr[i] - arr[i - k];
            if (sum > max_sum) {
                max_sum = sum;
                max_end = i;
            }
        }
        // Return starting index
        return max_end - k + 1;
    }
}
```