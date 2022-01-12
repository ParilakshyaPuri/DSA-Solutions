### Problem Link: https://leetcode.com/problems/sum-of-root-to-leaf-binary-numbers/

## Solution:
 ```
 class Solution {
public:
    int sumRootToLeaf(TreeNode* root, int val=0) {
        //int val = 0;
        if(!root){
            return 0;
        }
        val= (val * 2 + root->val);
        if(root->left == root->right) 
            return val;
        else
            return (sumRootToLeaf(root->left, val) + sumRootToLeaf(root->right, val));
        }
};
 ```
**Hope it helps ✨**
