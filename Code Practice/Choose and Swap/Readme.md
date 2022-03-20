## Choose and Swap
[🔗Goto](https://practice.geeksforgeeks.org/problems/choose-and-swap0531/1) 

```

```
<details>
<summary>Full Code</summary>

```java

```
</details>

```java
class Solution{
    String chooseandswap(String A){
        // Code Here
        char[] a = A.toCharArray();
        
        boolean[] isPresent = new boolean[26];
        boolean[] visited = new boolean[26];
        
        int n = A.length();
        for (char currentChar: a) {
            isPresent[currentChar - 'a'] = true;
        }
        
        for (char currentChar: a) {
            for (int j = 0 ; j < currentChar - 'a' ; j++) {
                if (isPresent[j] && !visited[j]) {
                    return swap(a, currentChar, (char)(j+'a'));
                }
            }
            visited[currentChar - 'a'] = true;
        }
        
        return A;
    }
    
    private String swap(char[] a, char x, char y) {
        for (int i = 0 ; i < a.length ; i++) {
            if (a[i] == x) {
                a[i] = y;
            } else if (a[i] == y) {
                a[i] = x;
            }
        }
        return new String(a);
    }
}
```
