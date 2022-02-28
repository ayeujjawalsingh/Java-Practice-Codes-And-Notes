## Maximum Product Subarray
Given an array Arr[] that contains N integers (may be positive, negative or zero). Find the product of the maximum product subarray. [🔗Goto](https://practice.geeksforgeeks.org/problems/maximum-product-subarray3604/0/?page=1&difficulty[]=1&status[]=unsolved&company[]=Amazon&sortBy=submissions#) 

```
Example 1:

Input:
N = 5
Arr[] = {6, -3, -10, 0, 2}
Output: 180
Explanation: Subarray with maximum product
is [6, -3, -10] which gives product as 180.

Example 2:

Input:
N = 6
Arr[] = {2, 3, 4, 5, -1, 0}
Output: 120
Explanation: Subarray with maximum product
is [2, 3, 4, 5] which gives product as 120.
```
<details>
<summary>Full Code</summary>

```java
import java.io.*;
import java.util.*;

  public class Main {

    public static void main(String[] args) throws Exception {
        BufferedReader br =
            new BufferedReader(new InputStreamReader(System.in));
        int tc = Integer.parseInt(br.readLine());
        while (tc-- > 0) {
            int n = Integer.parseInt(br.readLine());
            int[] arr = new int[n];
            String[] inputLine = br.readLine().split(" ");
            for (int i = 0; i < n; i++) {
                arr[i] = Integer.parseInt(inputLine[i]);
            }

            System.out.println(new Solution().maxProduct(arr, n));
        }
    }
}
// } Driver Code Ends


class Solution {
    // Function to find maximum product subarray
    long maxProduct(int[] arr, int n) {
        long min = arr[0];
        long max = arr[0];
        long ans = arr[0];
        
        for(int i=1; i<n; i++){
            if(arr[i]==0){
                min = 1;
                max = 1;
                continue;
            }
            long temp1 = arr[i] * min;
            long temp2 = arr[i] * max;
            max = Math.max(temp1,temp2);
            max = Math.max(max,arr[i]);
            min = Math.min(temp1,temp2);
            min = Math.min(arr[i],min);
            ans = Math.max(ans,max);
        }
        return ans;
    }
}
```
</details>

```java
class Solution {
    // Function to find maximum product subarray
    long maxProduct(int[] arr, int n) {
        long min = arr[0];
        long max = arr[0];
        long ans = arr[0];
        
        for(int i=1; i<n; i++){
            if(arr[i]==0){
                min = 1;
                max = 1;
                continue;
            }
            long temp1 = arr[i] * min;
            long temp2 = arr[i] * max;
            max = Math.max(temp1,temp2);
            max = Math.max(max,arr[i]);
            min = Math.min(temp1,temp2);
            min = Math.min(arr[i],min);
            ans = Math.max(ans,max);
        }
        return ans;
    }
}
```
