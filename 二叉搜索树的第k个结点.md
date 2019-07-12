**题目：**

给定一棵二叉搜索树，请找出其中的第k小的结点。例如， （5，3，7，2，4，6，8）    中，按结点数值大小顺序第三小结点的值为4。 

**题目解析：**

一般来说二叉搜索树的序列为其层次遍历序列

**解题思路：**

1.中序遍历二叉搜索树即可得到二叉搜索数数值从小到大排列的序列

2.中序遍历时，将以往的使用一个数组来保存结点数值，转换为使用数组保存结点

3.在中序遍历序列上定位索引为k-1的结点即可。

**代码：**

```c++
/*
struct TreeNode {
    int val;
    struct TreeNode *left;
    struct TreeNode *right;
    TreeNode(int x) :
            val(x), left(NULL), right(NULL) {
    }
};
*/
class Solution {
public:
    TreeNode* KthNode(TreeNode* pRoot, int k)
    {
        if(pRoot==NULL||k<=0){
            return NULL;
        }
        vector<TreeNode*> inSeries;
        inOrder(pRoot,inSeries);
        if(k>int(inSeries.size()))
            return NULL;
        return inSeries[k-1];
    }
    void inOrder(TreeNode* root,vector<TreeNode*> &vi){
        if(root==NULL)return;
        inOrder(root->left,vi);
        vi.push_back(root);
        inOrder(root->right,vi);
        
    }
    
};
```

