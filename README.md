# Playing-With-Binary-Trees
<h3>Multiple C++ codes which each perform specific tasks for binary trees</h3>
<br>

Function used to find the number of edges from the tree's root node to a selected node.
```
template <typename Object>
int Depth(TreeNode<Object>* root, TreeNode<Object>* node) {
    if (node != nullptr && root != nullptr) {
        if (root == node) return 0;
        else {
            if (root->firstChild != nullptr)
                return 1 + Depth(root->firstChild, node);
            else if (root->nextSibling != nullptr)
                return Depth(root->nextSibling, node);
        }
    }
}
```

Function used to find the number of edges on the longest downward path from a selected node to a leaf node.
```
template <typename Object>
int Height(TreeNode<Object>* root, TreeNode<Object>* node) {
    if (node == nullptr) 
        return 0;
    else if (root == node) {
        if (node->firstChild == nullptr)
            return 0;
        else
            Height(root, node->firstChild);
    }
    else {
        if ((1+Height(root, node->firstChild)) > (Height(root, node->nextSibling)))
            return 1 + Height(root, node->firstChild);
        else if ((1 + Height(root, node->firstChild)) < (Height(root, node->nextSibling)))
            return Height(root, node->nextSibling);
    } 
}
```

Function that prints the tree in <i>Infix</i> equivalent format 
```
template <typename Object>
void inFix(BinaryNode<Object>* node) {
    if (node == nullptr) return;
    else {
        inFix(node->left);
        cout << node->element;
        inFix(node->right);
    }
}
```

Function that prints the tree in <i>Postfix</i> equivalent format 
```
template <typename Object>
void postFix(BinaryNode<Object>* node) {
    if (node != nullptr) {
    postFix(node->left);
    postFix(node->right);
    cout << node->element << ' ';
    }
}
```

Function that prints the tree in <i>Prefix</i> equivalent format
```
template <typename Object>
void preFix(BinaryNode<Object>* node) {
    if (node != nullptr) {
        cout << node->element << ' ';
        preFix(node->left);
        preFix(node->right);
    }
}
```

