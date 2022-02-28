## Boundary Traversal of binary tree
Given a Binary Tree, find its Boundary Traversal. The traversal should be in the following order: 

Left boundary nodes: defined as the path from the root to the left-most node ie- the leaf node you could reach when you always travel preferring the left subtree over the right subtree. 
Leaf nodes: All the leaf nodes except for the ones that are part of left or right boundary.
Reverse right boundary nodes: defined as the path from the right-most node to the root. The right-most node is the leaf node you could reach when you always travel preferring the right subtree over the left subtree. Exclude the root from this as it was already included in the traversal of left boundary nodes.
Note: If the root doesn't have a left subtree or right subtree, then the root itself is the left or right boundary.  [🔗Goto](https://practice.geeksforgeeks.org/problems/boundary-traversal-of-binary-tree/1/?page=1&difficulty[]=1&status[]=unsolved&company[]=Amazon&sortBy=submissions#) 


<details>
<summary>Full Code</summary>

```java
import java.io.*;
import java.util.*;

class Node  
{ 
    int data; 
    Node left, right; 
   
    public Node(int d)  
    { 
        data = d; 
        left = right = null; 
    } 
}

class GFG
{
    static Node buildTree(String str)
    {
        // Corner Case
        if(str.length() == 0 || str.equals('N'))
            return null;
        String[] s = str.split(" ");
        
        Node root = new Node(Integer.parseInt(s[0]));
        Queue <Node> q = new LinkedList<Node>();
        q.add(root);
        
        // Starting from the second element
        int i = 1;
        while(!q.isEmpty() && i < s.length)
        {
              // Get and remove the front of the queue
              Node currNode = q.remove();
        
              // Get the current node's value from the string
              String currVal = s[i];
        
              // If the left child is not null
              if(!currVal.equals("N")) 
              {
        
                  // Create the left child for the current node
                  currNode.left = new Node(Integer.parseInt(currVal));
        
                  // Push it to the queue
                  q.add(currNode.left);
              }
        
              // For the right child
              i++;
              if(i >= s.length)
                  break;
              currVal = s[i];
        
              // If the right child is not null
              if(!currVal.equals("N")) 
              {
        
                  // Create the right child for the current node
                  currNode.right = new Node(Integer.parseInt(currVal));
        
                  // Push it to the queue
                  q.add(currNode.right);
              }
              
              i++;
        }
    
        return root;
    }
    
    public static void main(String args[]) throws IOException {
    
       BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int t = Integer.parseInt(br.readLine().trim());
        while(t>0)
        {
            String s = br.readLine();
            Node root = buildTree(s);
            
            Solution T = new Solution();
            
            ArrayList <Integer> res = T.boundary(root);
            for (Integer num : res) System.out.print (num + " ");
            System.out.println();
            t--;
        }
    }
}
// } Driver Code Ends


//User function Template for Java

// class Node  
// { 
//     int data; 
//     Node left, right; 
   
//     public Node(int d)  
//     { 
//         data = d; 
//         left = right = null; 
//     } 
// }

class Solution
{
	ArrayList <Integer> boundary(Node node)
	{
	    ArrayList<Integer> arr = new ArrayList<>();
	    if(!isLeafNode(node)){
	        arr.add(node.data);
	    }
	    addLeft(node, arr);
	    addLeaves(node, arr);
	    addRight(node, arr);
	    
	    return arr;
	}
	
	boolean isLeafNode(Node root){
	    return (root.left == null) && (root.right == null);
	}
	
	void addLeft(Node root, ArrayList<Integer> arr){
	    Node curr = root.left;
	    while(curr!=null){
	        if(!isLeafNode(curr)){
	            arr.add(curr.data);
	        }
	        if(curr.left!=null){
	            curr = curr.left;
	        }else{
	            curr = curr.right;
	        }
	    }
	}
	
	void addLeaves(Node root, ArrayList<Integer> arr){
	    if(isLeafNode(root)){
	        arr.add(root.data);
	        return;
	    }
	    if(root.left!=null){
	        addLeaves(root.left, arr);
	    }
	    if(root.right!=null){
	        addLeaves(root.right, arr);
	    }
	}
	
	void addRight(Node root, ArrayList<Integer> arr){
	    Node curr = root.right;
	    ArrayList<Integer> temp = new ArrayList<>();
	    while(curr!=null){
	        if(!isLeafNode(curr)){
	            temp.add(curr.data);
	        }
	        if(curr.right!=null){
	            curr = curr.right;
	        }
	        else{
	            curr = curr.left;
	        }
	    }
	    Collections.reverse(temp);
	    arr.addAll(temp);
	}
}
```
</details>

```java
class Solution
{
	ArrayList <Integer> boundary(Node node)
	{
	    ArrayList<Integer> arr = new ArrayList<>();
	    if(!isLeafNode(node)){
	        arr.add(node.data);
	    }
	    addLeft(node, arr);
	    addLeaves(node, arr);
	    addRight(node, arr);
	    
	    return arr;
	}
	
	boolean isLeafNode(Node root){
	    return (root.left == null) && (root.right == null);
	}
	
	void addLeft(Node root, ArrayList<Integer> arr){
	    Node curr = root.left;
	    while(curr!=null){
	        if(!isLeafNode(curr)){
	            arr.add(curr.data);
	        }
	        if(curr.left!=null){
	            curr = curr.left;
	        }else{
	            curr = curr.right;
	        }
	    }
	}
	
	void addLeaves(Node root, ArrayList<Integer> arr){
	    if(isLeafNode(root)){
	        arr.add(root.data);
	        return;
	    }
	    if(root.left!=null){
	        addLeaves(root.left, arr);
	    }
	    if(root.right!=null){
	        addLeaves(root.right, arr);
	    }
	}
	
	void addRight(Node root, ArrayList<Integer> arr){
	    Node curr = root.right;
	    ArrayList<Integer> temp = new ArrayList<>();
	    while(curr!=null){
	        if(!isLeafNode(curr)){
	            temp.add(curr.data);
	        }
	        if(curr.right!=null){
	            curr = curr.right;
	        }
	        else{
	            curr = curr.left;
	        }
	    }
	    Collections.reverse(temp);
	    arr.addAll(temp);
	}
}
```
