### Problem Link: https://leetcode.com/problems/insert-into-a-binary-search-tree/
<br>
###Solution: 
The solution is pretty straight forward.
- if val is less than root->val, then go left.
- if val is more than root->val, then go right.
- lastly, we need to insert at the empty apt space.
<br>
#### CODE:
```
class Solution {
public:
    TreeNode* insertIntoBST(TreeNode* root, int val) {
        //To insert at right space
        if(root== NULL)
            return new TreeNode(val);
    
        if(val< root->val){
            root->left= insertIntoBST(root->left, val);
        }
        else{
            root->right= insertIntoBST(root->right, val);
        }
        return root;
    }
};
```

**Hope it helps!! ✨**
