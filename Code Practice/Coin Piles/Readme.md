## Coin Piles
There are N piles of coins each containing  Ai (1<=i<=N) coins. Find the minimum number of coins to be removed such that the absolute difference of coins in any two piles is at most K.
Note: You can also remove a pile by removing all the coins of that pile. [🔗Goto](https://practice.geeksforgeeks.org/problems/coin-piles5152/1) 

```
Example 1:

Input:
N = 4, K = 0
arr[] = {2, 2, 2, 2}
Output:
0
Explanation:
For any two piles the difference in the
number of coins is <=0. So no need to
remove any coins. 

Example 2:
Input:
N = 6, K = 3
arr[] = {1, 5, 1, 2, 5, 1} 
Output :
2
Explanation:
If we remove one coin each from both
the piles containing 5 coins , then
for any two piles the absolute difference
in the number of coins is <=3. 
```
<details>
<summary>Full Code</summary>

```java


```
</details>

```java
class Solution {
    static int minSteps(int[] A, int N, int K) {
     Arrays.sort(A);
     
     int prefix[] = new int[N];
     prefix[0] = A[0];
     
     for(int i=1; i<N; i++)
        prefix[i] = prefix[i-1] + A[i];
     
     int ans = Integer.MAX_VALUE;   
     for(int i=0; i<N; i++){
        int ub = upper_bound(A, A[i]+K); 
        int ra = ub==-1 ? 0 : (prefix[N-1]-prefix[ub-1]) - (A[i]+K)*(N-ub);
        int la = i==0 ? 0 : prefix[i-1];
        ans = Integer.min(ans, la+ra);
     }
     
     return ans;
    }
    
     static int upper_bound(int arr[], int key)
    {
        int mid, N = arr.length;
        int low = 0;
        int high = N;
  
        while (low < high && low != N) {
            mid = low + (high - low) / 2;

            if (key >= arr[mid])low = mid + 1;
            else high = mid;
        }
  
        if (low == N )return -1;
        return low;
    }
};
```
