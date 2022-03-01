## Preorder traversal (Iterative) 
Given a binary tree. Find the preorder traversal of the tree without using recursion. [🔗Goto](https://practice.geeksforgeeks.org/problems/preorder-traversal-iterative/1/?page=4&difficulty[]=1&status[]=unsolved&sortBy=accuracy#) 

```
Example 1:

Input:
           1
         /   \
        2     3
      /  \
     4    5
Output: 1 2 4 5 3
Explanation:
Preorder traversal (Root->Left->Right) of 
the tree is 1 2 4 5 3.

Example 2

Input:
            8
          /   \
         1      5
          \    /  \
           7  10   6
            \  /
            10 6
Output: 8 1 7 10 5 10 6 6 
Explanation:
Preorder traversal (Root->Left->Right) 
of the tree is 8 1 7 10 5 10 6 6.
```
<details>
<summary>Full Code</summary>

```java
import java.util.LinkedList; 
import java.util.Queue; 
import java.io.*;
import java.util.*;

class Node{
    int data;
    Node left;
    Node right;
    Node(int data){
        this.data = data;
        left=null;
        right=null;
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
  
	public static void main (String[] args) throws IOException{
	        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
	        
	        int t=Integer.parseInt(br.readLine());
    
	        while(t > 0){
	            String s = br.readLine();
    	    	Node root = buildTree(s);
    	    	Tree g = new Tree();
                ArrayList<Integer> res = g.preOrder(root);
                for (int i = 0; i < res.size (); i++)
                    System.out.print (res.get (i) + " ");
                System.out.print("\n");
                t--;
        }
    }
}
// } Driver Code Ends


//User function Template for Java

/* A Binary Tree node 

class Node {
    int data;
    Node left, right;
   Node(int item)    {
        data = item;
        left = right = null;
    }
} */
class Tree
{
   // Return a list containing the inorder traversal of the given tree
   ArrayList<Integer> preOrder(Node root)
   {
       ArrayList<Integer> res=new ArrayList<>();
       Stack<Node> stack=new Stack<>();
       Node node=root;
       while(node!=null || stack.size()>0){
           while(node!=null){
               res.add(node.data);
               stack.push(node);
               node=node.left;
           }
           node=stack.pop();
           node=node.right;
       }
       return res;
   }
}
```
</details>

```java
//Without Using Recursion
class Tree
{
   // Return a list containing the inorder traversal of the given tree
   ArrayList<Integer> preOrder(Node root)
   {
       // Code
       ArrayList<Integer> res=new ArrayList<>();
       Stack<Node> stack=new Stack<>();
       Node node=root;
       while(node!=null || stack.size()>0)
       {
           while(node!=null)
           {
               res.add(node.data);
               stack.push(node);
               node=node.left;
           }
           node=stack.pop();
           node=node.right;
       }
       return res;
   }
}
```

```java
//Using Recursion
class Tree
{
    ArrayList<Integer> list = new ArrayList<Integer>();
    ArrayList<Integer> preOrder(Node root)
    {
        if(root!=null)
        list.add(root.data);
        if(root.left!=null)
        preOrder(root.left);
        if(root.right!=null)
        preOrder(root.right);
        return list;
    }
}
```