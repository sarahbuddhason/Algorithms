# Tree Traversals

1. **Preorder (Root, Left, Right)**:
   - Visit the root.
   - Traverse the left subtree.
   - Traverse the right subtree.
   - **Time**: O(n)
   - **Space**: O(h)

```
void preorder(Node* root) {
    if(!root) return;
    cout << root->data << " ";
    preorder(root->left);
    preorder(root->right);
}
```

2. **Inorder (Left, Root, Right)**:
   - Traverse the left subtree.
   - Visit the root.
   - Traverse the right subtree.
   - **Time**: O(n)
   - **Space**: O(h)

```
void preorder(Node* root) {
    if(!root) return;
    cout << root->data << " ";
    preorder(root->left);
    preorder(root->right);
}
```

3. **Postorder (Left, Right, Root)**:
   - Traverse the left subtree.
   - Traverse the right subtree.
   - Visit the root.
   - **Time**: O(n)
   - **Space**: O(h)

```
void postorder(Node* root) {
    if(!root) return;
    postorder(root->left);
    postorder(root->right);
    cout << root->data << " ";
}
```

4. **Level Order (or Breadth First)**:
   - Visit nodes level by level.
   - Dequeue node.
   - Enqueue left subtree.
   - Enqueue right subtree.
   - **Time**: O(n)
   - **Space**: O(n)

```
#include <queue>
void levelOrder(Node* root) {
    if(!root) return;
    queue<Node*> q;
    q.push(root);
    while(!q.empty()) {
        Node* curr = q.front();
        q.pop();
        cout << curr->data << " ";
        if(curr->left) q.push(curr->left);
        if(curr->right) q.push(curr->right);
    }
}
```

---

# Greedy Algorithm

Makes locally optimal choices at each step, aiming for a global optimum.

- **Complexity**:
  - **Time**: Often O(n) or O(n log n).
  - **Space**: Usually O(n).
