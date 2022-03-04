## Bottom View of Binary Tree
Given a binary tree, print the bottom view from left to right.
A node is included in bottom view if it can be seen when we look at the tree from bottom.

                      20
                    /    \
                  8       22
                /   \        \
              5      3       25
                    /   \      
                  10    14

For the above tree, the bottom view is 5 10 3 14 25.
If there are multiple bottom-most nodes for a horizontal distance from root, then print the later one in level traversal. For example, in the below diagram, 3 and 4 are both the bottommost nodes at horizontal distance 0, we need to print 4.

                      20
                    /    \
                  8       22
                /   \     /   \
              5      3 4     25
                     /    \      
                 10       14

For the above tree the output should be 5 10 4 14 25. [🔗Goto](https://practice.geeksforgeeks.org/problems/bottom-view-of-binary-tree/1/?page=2&difficulty[]=1&status[]=unsolved&sortBy=submissions#) 

```
Example 1:

Input:
       1
     /   \
    3     2
Output: 3 1 2
Explanation:
First case represents a tree with 3 nodes
and 2 edges where root is 1, left child of
1 is 3 and right child of 1 is 2.

Example 2:

Input:
         10
       /    \
      20    30
     /  \
    40   60
Output: 40 20 60 30
```
<details>
<summary>Full Code</summary>

```java
import java.util.LinkedList; 
import java.util.Queue; 
import java.io.*;
import java.util.*;

class Node
{
    int data; //data of the node
    int hd; //horizontal distance of the node
    Node left, right; //left and right references
 
    // Constructor of tree node
    public Node(int key)
    {
        data = key;
        hd = Integer.MAX_VALUE;
        left = right = null;
    }
}



class GfG {
    
    static Node buildTree(String str){
        
        if(str.length()==0 || str.charAt(0)=='N'){
            return null;
        }
        
        String ip[] = str.split(" ");
        // Create the root of the tree
        Node root = new Node(Integer.parseInt(ip[0]));
        // Push the root to the queue
        
        Queue<Node> queue = new LinkedList<>(); 
        
        queue.add(root);
        // Starting from the second element
        
        int i = 1;
        while(queue.size()>0 && i < ip.length) {
            
            // Get and remove the front of the queue
            Node currNode = queue.peek();
            queue.remove();
                
            // Get the current node's value from the string
            String currVal = ip[i];
                
            // If the left child is not null
            if(!currVal.equals("N")) {
                    
                // Create the left child for the current node
                currNode.left = new Node(Integer.parseInt(currVal));
                // Push it to the queue
                queue.add(currNode.left);
            }
                
            // For the right child
            i++;
            if(i >= ip.length)
                break;
                
            currVal = ip[i];
                
            // If the right child is not null
            if(!currVal.equals("N")) {
                    
                // Create the right child for the current node
                currNode.right = new Node(Integer.parseInt(currVal));
                    
                // Push it to the queue
                queue.add(currNode.right);
            }
            i++;
        }
        
        return root;
    }
    static void printInorder(Node root)
    {
        if(root == null)
            return;
            
        printInorder(root.left);
        System.out.print(root.data+" ");
        
        printInorder(root.right);
    }
    
	public static void main (String[] args) throws IOException{
	        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
	        
	        int t=Integer.parseInt(br.readLine());
    
	        while(t-- > 0){
	            String s = br.readLine();
    	    	Node root = buildTree(s);
    	        Solution ob = new Solution();
			    ArrayList <Integer> res = ob.bottomView(root);
			    for (Integer num : res) System.out.print (num + " ");
		     	System.out.println();
	        }
	}
}

// } Driver Code Ends


//User function Template for Java


class Solution
{
    //Function to return a list containing the bottom view of the given tree.
    public ArrayList <Integer> bottomView(Node root)
    {
        ArrayList<Integer> ans = new ArrayList<>(); 
        if(root == null) return ans;
        Map<Integer, Integer> map = new TreeMap<>();
        Queue<Node> q = new LinkedList<Node>();
        root.hd = 0;
        q.add(root); 
        while(!q.isEmpty()) {
            Node temp = q.remove();
            int hd = temp.hd; 
            map.put(hd, temp.data); 
            if(temp.left != null) {
                temp.left.hd = hd - 1; 
                q.add(temp.left); 
            }
            if(temp.right != null) {
                temp.right.hd = hd + 1; 
                q.add(temp.right); 
            }
        }
        
        for (Map.Entry<Integer,Integer> entry : map.entrySet()) {
            ans.add(entry.getValue()); 
        }
        return ans;
    }
}
```
</details>

```java
//Approach 1

class Solution
{
    //Function to return a list containing the bottom view of the given tree.
    public ArrayList <Integer> bottomView(Node root)
    {
        ArrayList<Integer> ans = new ArrayList<>(); 
        if(root == null) return ans;
        Map<Integer, Integer> map = new TreeMap<>();
        Queue<Node> q = new LinkedList<Node>();
        root.hd = 0;
        q.add(root); 
        while(!q.isEmpty()) {
            Node temp = q.remove();
            int hd = temp.hd; 
            map.put(hd, temp.data); 
            if(temp.left != null) {
                temp.left.hd = hd - 1; 
                q.add(temp.left); 
            }
            if(temp.right != null) {
                temp.right.hd = hd + 1; 
                q.add(temp.right); 
            }
        }
        
        for (Map.Entry<Integer,Integer> entry : map.entrySet()) {
            ans.add(entry.getValue()); 
        }
        return ans;
    }
}
```

```java
//Approach 2

class Solution
{
    /*
    only the element at each coordinate which are at the max height for that coordinate are
    printed
    tree stores a hashmap that stores the coordinate as the key and an arraylist as the value
    the arraylist stores the value as the first element and the height as the second element
    the map function goes through the entire tree and updates each coordinate in the tree map
    finally the coordinates arraylist is sorted which prints the elements that can be seen from
    the bottom
    */
    
    HashMap<Integer, ArrayList<Integer>> tree = new HashMap<>();
    ArrayList<Integer> coordinates = new ArrayList<>();
    public ArrayList <Integer> bottomView(Node root)
    {
        mapTree(root, 0, 1);
        Collections.sort(coordinates);
        ArrayList<Integer> res = new ArrayList<>();
        for(Integer coordinate : coordinates){
            ArrayList<Integer> temp = tree.get(coordinate);
            res.add(temp.get(0));
        }
        return res;
    }
    void mapTree(Node root, int coordinate, int level){
        if(root==null)
            return;
        if(tree.containsKey(coordinate)){
            ArrayList<Integer> temp = tree.get(coordinate);
            if(level>=temp.get(1)){
                temp.remove(1);
                temp.remove(0);
                temp.add(root.data);
                temp.add(level);
            }
        }
        else{
            ArrayList<Integer> temp = new ArrayList<>();
            temp.add(root.data);
            temp.add(level);
            tree.put(coordinate,temp);
            coordinates.add(coordinate);
        }
        mapTree(root.left,coordinate-1, level+1);
        mapTree(root.right, coordinate+1, level+1);
    }
}

```