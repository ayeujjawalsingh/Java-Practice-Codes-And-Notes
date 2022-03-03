## Rotate and delete
Given a N x N 2D matrix Arr representing an image. Rotate the image by 90 degrees (anti-clockwise). You need to do this in place. Note that if you end up using an additional array, you will only receive partial score.[🔗Goto](https://practice.geeksforgeeks.org/problems/rotate-a-2d-array-without-using-extra-space1004/1/?page=2&difficulty[]=1&status[]=unsolved&category[]=Arrays&category[]=Strings&sortBy=accuracy) 

```
Example 1:

Input:
N = 3
Arr[][] = {{1,  2,  3}
           {4,  5,  6}
           {7,  8,  9}}
Output:
 3  6  9 
 2  5  8 
 1  4  7 
Explanation: The given matrix is rotated
by 90 degree in anti-clockwise direction.

Example 2:

Input:
N = 4
Arr[][] = {{1,  2,  3,  4}
           {5,  6,  7,  8}
           {9, 10, 11, 12}
           {13, 14, 15, 16}}
Output:
 4  8 12 16 
 3  7 11 15 
 2  6 10 14 
 1  5  9 13
Explanation: The given matrix is rotated
by 90 degree in anti-clockwise direction.
```
<details>
<summary>Full Code</summary>

```java
import java.util.*;
import java.io.*;

public class Main {

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        PrintWriter out = new PrintWriter(System.out);
        int tc = Integer.parseInt(br.readLine().trim());
        while (tc-- > 0) {
            String[] inputLine;
            int n = Integer.parseInt(br.readLine().trim());
            int[][] arr = new int[n][n];
            inputLine = br.readLine().trim().split(" ");
            for (int i = 0; i < n; i++) {
                for (int j = 0; j < n; j++) {
                    arr[i][j] = Integer.parseInt(inputLine[i * n + j]);
                }
            }

            new Solution().rotateMatrix(arr, n);
            for (int i = 0; i < n; i++) {
                for (int j = 0; j < n; j++) {
                    out.print(arr[i][j] + " ");
                }
            }
            out.println();
        }
        out.flush();
    }
}// } Driver Code Ends


//User function Template for Java



class Solution {
    void rotateMatrix(int matrix[][], int n) {
        // code here
        // int n = matrix.length;
        for(int i=0;i<n;i++){  
            for(int j=i;j<n;j++){
                int temp = matrix[i][j];
                matrix[i][j] = matrix[j][i];
                matrix[j][i] = temp;
            }
        }
        for(int i=0;i<n;i++){ 
            int low = 0;  
            int high = n-1;  
            while(low < high){  
                int temp = matrix[low][i];  
                matrix[low][i] = matrix[high][i];  
                matrix[high][i] = temp;  
                low++;  
                high--;
            }
        }  
    }
}
```
</details>

```java
class Solution {
    void rotateMatrix(int matrix[][], int n) {
        for(int i=0;i<n;i++){  
            for(int j=i;j<n;j++){
                int temp = matrix[i][j];
                matrix[i][j] = matrix[j][i];
                matrix[j][i] = temp;
            }
        }
        for(int i=0;i<n;i++){ 
            int low = 0;  
            int high = n-1;  
            while(low < high){  
                int temp = matrix[low][i];  
                matrix[low][i] = matrix[high][i];  
                matrix[high][i] = temp;  
                low++;  
                high--;
            }
        }  
    }
}
```
