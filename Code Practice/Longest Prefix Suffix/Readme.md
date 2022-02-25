## Longest Prefix Suffix
Given a string of characters, find the length of the longest proper prefix which is also a proper suffix.

NOTE: Prefix and suffix can be overlapping but they should not be equal to the entire string. [🔗Goto](https://practice.geeksforgeeks.org/problems/longest-prefix-suffix2527/1/?page=4) 

<details>
<summary>Full Code</summary>

```java
import java.io.*;
import java.util.*;

class GFG {
    public static void main(String args[]) throws IOException {
        BufferedReader read =
            new BufferedReader(new InputStreamReader(System.in));
        int t = Integer.parseInt(read.readLine());
        while (t-- > 0) {
            
            String s = read.readLine();
            Solution ob = new Solution();
            System.out.println(ob.lps(s));
        }
    }
}// } Driver Code Ends


//User function Template for Java

class Solution {
    int lps(String s) {
        int i=1,len=0;
        int lps[]=new int[s.length()];
        while(i<s.length()){
            if(s.charAt(i)==s.charAt(len)){
                len++;
                lps[i++]=len;
             }else{
                if(len>0)  len=lps[len-1];
                else lps[i++]=0;
            }
        }
        return lps[s.length()-1];
    }
}
```
</details>

```java
class Solution {
    int lps(String s) {
        int i=1,len=0;
        int lps[]=new int[s.length()];
        while(i<s.length()){
            if(s.charAt(i)==s.charAt(len)){
                len++;
                lps[i++]=len;
             }else{
                if(len>0)  len=lps[len-1];
                else lps[i++]=0;
            }
        }
        return lps[s.length()-1];
    }
}
```