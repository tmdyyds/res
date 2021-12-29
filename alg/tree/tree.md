## 前序遍历

> 节点 > 左子树 > 右子树
>
> 前序遍历的递推公式：preOrder(r) = print r->preOrder(r->left)->preOrder(r->right)

## 中序遍历

> 左子树 > 节点 > 右子树
>
> 中序遍历的递推公式：inOrder(r) = inOrder(r->left)->print r->inOrder(r->right)

## 后续遍历

> 左子树 > 右子树 > 节点
>
> 后序遍历的递推公式：postOrder(r) = postOrder(r->left)->postOrder(r->right)->print r