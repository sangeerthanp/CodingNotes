# [450. Delete Node in a BST](https://leetcode.com/problems/delete-node-in-a-bst/)

```java
class Solution {

    public int min(TreeNode root){
        int min = -1;
        while(root != null){
            min = root.val;
            root = root.left;
        }
        return min;
    }

  
    public TreeNode deleteNode(TreeNode root, int key) {

        if(root == null) return null;

        if(key < root.val){
            root.left = deleteNode(root.left,key);
        }else if(key > root.val){
            root.right = deleteNode(root.right,key);
        }else{
            if(root.left == null) return root.right;
            else if(root.right == null) return root.left;
            else{
                root.val = min(root.right);
                root.right = deleteNode(root.right,root.val);
            }
        }
        return root;
    }
}
```


# [701. Insert into a Binary Search Tree](https://leetcode.com/problems/insert-into-a-binary-search-tree/)

```java
class Solution {

    public TreeNode insertIntoBST(TreeNode root, int val) {

        if(root == null) return new TreeNode(val);

        if(val < root.val){
            root.left = insertIntoBST(root.left,val);
        }else{
            root.right = insertIntoBST(root.right,val);
        }

        return root;
    }
}
```

# [700. Search in a Binary Search Tree](https://leetcode.com/problems/search-in-a-binary-search-tree/)

```java
class Solution {

    public TreeNode searchBST(TreeNode root, int val) {

        if(root == null) return null;

        if(root.val == val){
            return root;
        }
  
        if(val < root.val){
            return searchBST(root.left,val); 
        }else{
            return searchBST(root.right,val);
        }
    }
}
```

