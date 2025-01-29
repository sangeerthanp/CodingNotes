
# Implementation

```java
import java.util.ArrayList;
import java.util.List;

  

public class NaryTreePractice {
    private static class TreeNode {
        int val;
        List<TreeNode> children;
        
        TreeNode(int data) {
            this.val = data;
            this.children = new ArrayList<>();
        }
    }

  
    TreeNode root;
  
    NaryTreePractice() { // represents the whoel treee
        this.root = null;
    }


    void constructTree() {

        this.root = new TreeNode(1);


        this.root.children.add(new TreeNode(2));
        this.root.children.get(0).children.add(new TreeNode(3));
        this.root.children.get(0).children.add(new TreeNode(4));
        this.root.children.get(0).children.add(new TreeNode(6));

        this.root.children.add(new TreeNode(5));
        this.root.children.get(1).children.add(new TreeNode(7));

        this.root.children.add(new TreeNode(8));
        this.root.children.get(2).children.add(new TreeNode(9));
        this.root.children.get(2).children.add(new TreeNode(11));

    }

  

    public void preOrderTraversal(TreeNode root) {
        if (root == null)
            return;
        System.out.print(root.val + " ");
        for (TreeNode child : root.children) {
            preOrderTraversal(child);
        }
    }


    public void postOrderTraversal(TreeNode root) {
        if (root == null)
            return;
        for (TreeNode child : root.children) {
            postOrderTraversal(child);
        }
        System.out.print(root.val + " ");
    }


    public void inOrderTraversal(TreeNode root) {
        if (root == null)
            return;
        int len = root.children.size();
        for (int i = 0; i < len - 1; i++) {
            inOrderTraversal(root.children.get(i))
        }
        System.out.print(root.val + " ");
        if (len > 0)
            inOrderTraversal(root.children.get(len - 1));
    }

      public void levelOrder(TreeNode root, List<List<Integer>> list) {

        Queue<TreeNode> queue = new LinkedList<>();
        queue.add(root);


        while (!queue.isEmpty()) {
            int size = queue.size();
            List<Integer> l = new ArrayList<>();

            for (int i = 0; i < size; i++) {
                TreeNode node = queue.poll();
                l.add(node.val);

                for (TreeNode child : node.children) {
                    queue.add(child);
                }
            }
            list.add(l);
        }
    }

    public static void main(String[] args) {
    
        NaryTreePractice tree = new NaryTreePractice();
        tree.constructTree();
        tree.preOrderTraversal(tree.root);
        System.out.println();
        tree.postOrderTraversal(tree.root);
        System.out.println();
        tree.inOrderTraversal(tree.root);
        System.out.println();
        List<List<Integer>> list = new ArrayList<>();
        tree.levelOrder(tree.root, list);
        System.out.println(list);
    }
}
```


| PreOrder Traversal  | 1 2 3 4 6 5 7 8 9 11 |
| ------------------- | -------------------- |
| PostOrder Traversal | 3 4 6 2 7 5 9 11 8 1 |
| InOrder Traversal   | 3 4 2 6 5 7 1 9 8 11 |
# [559. Maximum Depth of N-ary Tree](https://leetcode.com/problems/maximum-depth-of-n-ary-tree/)

```java
class Solution {

    public int maxDepth(Node root) {

		------BFS------
    
        // if(root == null) return 0;
        
        // Queue<Node> queue = new LinkedList<>();
        // queue.add(root);

        // int level = 0;

        // while(!queue.isEmpty()){
        //     int size = queue.size();
        //     for(int i=0;i<size;i++){
        //         Node node = queue.poll();
        //         for(Node child : node.children){
        //             queue.add(child);
        //         }
        //     }
        //     level++;
        // }
        // return level;

        ------DFS------
        
        if(root == null) return 0;


        int level = 0;
        for(Node child : root.children){
            level = Math.max(level,maxDepth(child));
        }
        return level + 1;
    }
}
```


# To get sum of all nodes in a tree

```java
    public int getSum(TreeNode root, int sum) {

        if (root == null)
            return 0;

        sum = root.val;

        for (TreeNode child : root.children) {
            sum += getSum(child, sum);
        }

        return sum;
    }
```

