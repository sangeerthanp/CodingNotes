# [144. Binary Tree Preorder Traversal](https://leetcode.com/problems/binary-tree-preorder-traversal/)


```java
class Solution {
    ArrayList<Integer> list;
    public void preOrder(TreeNode root){

        if(root == null) return;

        list.add(root.val);

        preOrder(root.left);

        preOrder(root.right);
    }    

    public List<Integer> preorderTraversal(TreeNode root) {

        list = new ArrayList<>();

        preOrder(root);

        return list;
    }
}
```

# [145. Binary Tree Postorder Traversal](https://leetcode.com/problems/binary-tree-postorder-traversal/)

```java
class Solution {
    ArrayList<Integer> list;
    void postOrder(TreeNode root){

        if(root == null) return;

        postOrder(root.left);
        postOrder(root.right);
        list.add(root.val);

    }

    public List<Integer> postorderTraversal(TreeNode root) {
        list = new ArrayList<>();
        postOrder(root);
        return list;
    }
}
```

# [94. Binary Tree Inorder Traversal](https://leetcode.com/problems/binary-tree-inorder-traversal/)

```java
class Solution {
    public void inOrder(TreeNode root,ArrayList<Integer> list){

        if(root == null) return;


        inOrder(root.left,list);

        list.add(root.val);

        inOrder(root.right,list);

    }

    public List<Integer> inorderTraversal(TreeNode root) {

        ArrayList<Integer> list = new ArrayList<>();

        inOrder(root,list);

        return list;

    }

}
```


# [102. Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/)

```java
class Solution {

    public List<List<Integer>> levelOrder(TreeNode root) {

        List<List<Integer>> list = new ArrayList<>();
        if(root == null) return list;
        Queue<TreeNode> queue = new LinkedList<>();
        queue.offer(root);

        while(!queue.isEmpty()){
            int size = queue.size();
            List<Integer> l = new ArrayList<>();
            for(int i=0;i<size;i++){
                TreeNode node = queue.poll();
                l.add(node.val);
                if(node.left != null) queue.add(node.left);
                if(node.right != null) queue.add(node.right);
            }
            list.add(l);
        }
        return list;
    }
}
```


# [104. Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/)

```java
class Solution {

    public int maxDepth(TreeNode root) {
        if(root == null) return 0;
        Queue<TreeNode> queue = new LinkedList<>();
        queue.add(root);
        int depth = 0;

        while(!queue.isEmpty()){
            int size = queue.size();
            for(int i=0;i<size;i++){
                TreeNode node = queue.poll();
                if(node.left != null) queue.add(node.left);
                if(node.right != null) queue.add(node.right);
            }
            depth++;
        }
        return depth;
    }
}
```


# [100. Same Tree](https://leetcode.com/problems/same-tree/)

```java
class Solution {
    public boolean isSameTree(TreeNode p, TreeNode q) {

        if(p == null && q == null){
            return true;
        }

        if(p == null || q == null || p.val != q.val){
            return false;
        }  

        return isSameTree(p.left,q.left) && isSameTree(p.right,q.right);
    }
}
```

# [112. Path Sum](https://leetcode.com/problems/path-sum/)

```java
class Solution {

    public boolean getPreOrder(TreeNode root, int targetSum,int curr){

        if(root == null) return false;

        int sum = root.val + curr;

        if(sum == targetSum && root.left == null && root.right == null) return true;

        return getPreOrder(root.left,targetSum,sum) || getPreOrder(root.right,targetSum,sum);

    }

  

    public boolean hasPathSum(TreeNode root, int targetSum) {
        boolean res = getPreOrder(root,targetSum,0);
        if(res == true){
            return true;
        }else{
            return false;
        }
    }
}
```


# [199. Binary Tree Right Side View](https://leetcode.com/problems/binary-tree-right-side-view/)

```java
class Solution {

    public List<Integer> rightSideView(TreeNode root) {
        Queue<TreeNode> queue = new LinkedList<>();
        List<Integer> list = new ArrayList<>();

        if(root == null) return list;
        queue.add(root);

  
        while(!queue.isEmpty()){
            int size = queue.size();
            for(int i=0;i<size;i++){
                TreeNode node = queue.poll();
                
                if(i == size-1) list.add(node.val);
                if(node.left != null ) queue.add(node.left);
                if(node.right != null) queue.add(node.right);
            }
        }
        return list;
    }
}
```


# [Left View of Binary Tree](https://www.geeksforgeeks.org/problems/left-view-of-binary-tree/1)


```java
class Solution {
    // Function to return list containing elements of left view of binary tree.
    ArrayList<Integer> leftView(Node root) {
        Queue<Node> queue = new LinkedList<>();
        ArrayList<Integer> list = new ArrayList<>();
        if(root == null) return list;
        queue.add(root);

        while(!queue.isEmpty()){
            int size = queue.size();
            for(int i=0;i<size;i++){
                Node node = queue.poll();
                if(i == 0) list.add(node.data);
                if(node.left != null ) queue.add(node.left);
                if(node.right != null) queue.add(node.right);
            }
        }
        return list;
    }
}
```



# [236. Lowest Common Ancestor of a Binary Tree](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/)

```java
class Solution {

    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {

        if(root == null) return null;

        if(root == p || root == q) return root;


        TreeNode left = lowestCommonAncestor(root.left,p,q);
        TreeNode right = lowestCommonAncestor(root.right,p,q);

  
        if(left != null && right != null) return root;

        return left == null ? right : left;

    }

}
```

# [226. Invert Binary Tree](https://leetcode.com/problems/invert-binary-tree/)

```java
class Solution {

    public TreeNode invertTree(TreeNode root) {

        if(root == null) return null;

        Queue<TreeNode> queue = new LinkedList<>();
        queue.add(root);

        while(!queue.isEmpty()){
            TreeNode node = queue.poll();

            TreeNode left = node.left;
            node.left = node.right;
            node.right = left;

            if(node.left != null) queue.add(node.left);
            if(node.right != null) queue.add(node.right);
        }
        return root;
    }
}
```

# [101. Symmetric Tree](https://leetcode.com/problems/symmetric-tree/)

```java
class Solution {

    public boolean isSymmetric(TreeNode left,TreeNode right){

        if(left == null && right == null) return true;

        if(left == null || right == null || left.val != right.val) return false;

        return isSymmetric(left.left,right.right) && isSymmetric(left.right,right.left);

    }


    public boolean isSymmetric(TreeNode root) {

        if(root == null) return true;

        return isSymmetric(root.left,root.right);
    }
}
```

