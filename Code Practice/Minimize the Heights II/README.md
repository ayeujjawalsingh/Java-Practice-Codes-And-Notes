## Minimize the Heights II
Given an array arr[] denoting heights of N towers and a positive integer K, you have to modify the height of each tower either by increasing or decreasing them by K only once. After modifying, height should be a non-negative integer. 
Find out the minimum possible difference of the height of shortest and longest towers after you have modified each tower.

You can find a slight modification of the problem here.
Note: It is compulsory to increase or decrease (if possible) by K to each tower. [🔗Goto](https://practice.geeksforgeeks.org/problems/minimize-the-heights3351/1/?page=1) 

<details>
<summary>Full Code</summary>

```
import java.io.*;
import java.util.*;

  public class Main {

    public static void main(String[] args) throws Exception {
        BufferedReader br =
            new BufferedReader(new InputStreamReader(System.in));
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

            int ans = new Solution().getMinDiff(arr, n, k);
            System.out.println(ans);
        }
    }
}// } Driver Code Ends


// User function Template for Java

class Solution {
    static class Pair {
        int first, second;
        Pair(int x, int y) {
            first = x;
            second = y;
        }
    }
    int getMinDiff(int[] arr, int n, int k) {
        ArrayList<Pair> v = new ArrayList<Pair>();

        int[] taken = new int[n];

        // we will store all possible heights in a vector
        for (int i = 0; i < n; i++) {
            if (arr[i] - k >= 0) {
                v.add(new Pair(arr[i] - k, i));
            }
            v.add(new Pair(arr[i] + k, i));
        }

        Collections.sort(v, new Comparator<Pair>() {
            @Override   public int compare(Pair p1, Pair p2) {
                if (p1.first == p2.first) return p1.second - p2.second;
                return p1.first - p2.first;
            }
        });

        int elements_in_range = 0;
        int left = 0;
        int right = 0;

        // By two pointer we will traverse v and whenever we will get a range
        // in which all towers are included, we will update the answer.
        while (elements_in_range < n && right < v.size()) {
            if (taken[v.get(right).second] == 0) {
                elements_in_range++;
            }
            taken[v.get(right).second]++;
            right++;
        }
        int ans = v.get(right - 1).first - v.get(left).first;
        while (right < v.size()) {
            if (taken[v.get(left).second] == 1) {
                elements_in_range--;
            }
            taken[v.get(left).second]--;
            left++;

            while (elements_in_range < n && right < v.size()) {
                if (taken[v.get(right).second] == 0) {
                    elements_in_range++;
                }
                taken[v.get(right).second]++;
                right++;
            }

            if (elements_in_range == n) {
                ans = Math.min(ans, v.get(right - 1).first - v.get(left).first);
            } else
                break;
        }
        return ans;
    }
}
```
</details>

```
class Solution {
    static class Pair {
        int first, second;
        Pair(int x, int y) {
            first = x;
            second = y;
        }
    }
    int getMinDiff(int[] arr, int n, int k) {
        ArrayList<Pair> v = new ArrayList<Pair>();

        int[] taken = new int[n];

        // we will store all possible heights in a vector
        for (int i = 0; i < n; i++) {
            if (arr[i] - k >= 0) {
                v.add(new Pair(arr[i] - k, i));
            }
            v.add(new Pair(arr[i] + k, i));
        }

        Collections.sort(v, new Comparator<Pair>() {
            @Override   public int compare(Pair p1, Pair p2) {
                if (p1.first == p2.first) return p1.second - p2.second;
                return p1.first - p2.first;
            }
        });

        int elements_in_range = 0;
        int left = 0;
        int right = 0;

        // By two pointer we will traverse v and whenever we will get a range
        // in which all towers are included, we will update the answer.
        while (elements_in_range < n && right < v.size()) {
            if (taken[v.get(right).second] == 0) {
                elements_in_range++;
            }
            taken[v.get(right).second]++;
            right++;
        }
        int ans = v.get(right - 1).first - v.get(left).first;
        while (right < v.size()) {
            if (taken[v.get(left).second] == 1) {
                elements_in_range--;
            }
            taken[v.get(left).second]--;
            left++;

            while (elements_in_range < n && right < v.size()) {
                if (taken[v.get(right).second] == 0) {
                    elements_in_range++;
                }
                taken[v.get(right).second]++;
                right++;
            }

            if (elements_in_range == n) {
                ans = Math.min(ans, v.get(right - 1).first - v.get(left).first);
            } else
                break;
        }
        return ans;
    }
}
```