## Tree Traversals

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

## Greedy

Makes locally optimal choices at each step, aiming for a global optimum.

- **Complexity**:
  - **Time**: Often O(n) or O(n log n).
  - **Space**: Usually O(n).

 ---

 ## Breadth First Search

- Searches level by level.
- Uses a queue.
- **Time**: O(V + E) [V: vertices, E: edges]
- **Space**: O(V)

```
vector<bool> visited;
vector<vector<int>> adj; // adjacency list

void bfs(int start) {
    queue<int> q;
    visited[start] = true;
    q.push(start);

    while(!q.empty()) {
        int vertex = q.front();
        q.pop();
        // Process vertex

        for(int i : adj[vertex]) {
            if(!visited[i]) {
                visited[i] = true;
                q.push(i);
            }
        }
    }
}
```

---

## Depth First Search

- Searches by exploring as far as possible along a branch and then backtracks.
- Uses a stack or recursion.
- **Time**: O(V + E) [V: vertices, E: edges]
- **Space**: O(V)

```
vector<bool> visited;
vector<vector<int>> adj; // adjacency list

void dfs(int vertex) {
    visited[vertex] = true;
    // Process vertex

    for(int i : adj[vertex]) {
        if(!visited[i]) {
            dfs(i);
        }
    }
}
```

---
