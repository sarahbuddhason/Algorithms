# Algorithms
- [Tree Traversals](#tree-traversals)
- [Greedy](#greedy)
- [Breadth First Search](#breadth-first-search)
- [Depth First Search](#depth-first-search)
- [Dynamic Programming](#dynamic-programming)
- [1D vs. 2D Dynamic Programming](#1d-vs-2d-dynamic-programming)
- [Backtracking](#backtracking)

---

## Tree Traversals

### Preorder (Root, Left, Right)

- Visit the root.
- Traverse the left subtree.
- Traverse the right subtree.
- **Time**: O(n)
- **Space**: O(h)

```cpp
void preorder(Node* root) {
    if(!root) return;
    cout << root->data << " ";
    preorder(root->left);
    preorder(root->right);
}
```

### Inorder (Left, Root, Right)

- Traverse the left subtree.
- Visit the root.
- Traverse the right subtree.
- **Time**: O(n)
- **Space**: O(h)

```cpp
void preorder(Node* root) {
    if(!root) return;
    cout << root->data << " ";
    preorder(root->left);
    preorder(root->right);
}
```

### Postorder (Left, Right, Root)

- Traverse the left subtree.
- Traverse the right subtree.
- Visit the root.
- **Time**: O(n)
- **Space**: O(h)

```cpp
void postorder(Node* root) {
    if(!root) return;
    postorder(root->left);
    postorder(root->right);
    cout << root->data << " ";
}
```

### Level Order (or Breadth First)

- Visit nodes level by level.
- Dequeue node.
- Enqueue left subtree.
- Enqueue right subtree.
- **Time**: O(n)
- **Space**: O(n)

```cpp
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

- Makes locally optimal choices at each step, aiming for a global optimum.
- **Time**: Often O(n) or O(n log n).
- **Space**: Usually O(n).

 ---

## Breadth First Search

- Searches level by level.
- Uses a queue.
- **Time**: O(V + E)
- **Space**: O(V)

```cpp
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
- **Time**: O(V + E)
- **Space**: O(V)

```cpp
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

## Dynamic Programming

- Solves complex problems by breaking them into simpler subproblems.
  
### Memoization

- Top-down DP approach.
- Uses recursion and stores results of subproblems in a cache to avoid redundant computations.
  
```cpp
int fib_memo(int n, int memo[]) {
    if (memo[n] != -1) return memo[n];
    if (n <= 1) return n;
    memo[n] = fib_memo(n-1, memo) + fib_memo(n-2, memo);
    return memo[n];
}
```

### Tabulation

- Bottom-up DP approach.
- Builds a table in a bottom-up fashion to obtain the solution to the main problem.

```cpp
int fib_tab(int n) {
    int dp[n+1];
    dp[0] = 0; dp[1] = 1;
    for (int i = 2; i <= n; i++) {
        dp[i] = dp[i-1] + dp[i-2];
    }
    return dp[n];
}
```

```cpp
int main() {
    const int N = 10;
    int memo[N+1] = {-1};
    int result_memo = fib_memo(N, memo);
    int result_tab = fib_tab(N);
}
```

---

## 1D vs. 2D Dynamic Programming

### Applications (1D)

- **Fibonacci**: nth Fibonacci number.
- **Rod Cutting**: Max price by cutting a rod.
- **Coin Change**: Min coins for a total.
- **LIS**: Longest increasing subsequence length.

### Applications (2D)

- **LCS**: Longest common subsequence.
- **Matrix Multiplication**: Min operations to multiply matrices.
- **Knapsack**: Max value in knapsack of fixed capacity.
- **Edit Distance**: Min edits to transform one string to another.
- **Grid Path**: Shortest path in a 2D grid.
- **Palindromic Subs**: Longest palindromic substring or subsequence.

**Notes**:
- 1D DP considers a single aspect.
   - Single string, array.
- 2D DP involves combinations or relations between two aspects.
   - Two strings, a matrix, two sequences.

---

## Backtracking

- Solve problems by trying out solutions.
- If not feasible, undo (or "backtrack") and try another path.

```cpp
// N-Queens: place N queens on an N×N chessboard so that no two queens threaten each other.

bool isSafe(int board[][10], int row, int col, int N) {
    for (int i = 0; i < col; i++)
        if (board[row][i]) return false;
    for (int i = row, j = col; i >= 0 && j >= 0; i--, j--)
        if (board[i][j]) return false;
    for (int i = row, j = col; j >= 0; i++, j--)
        if (board[i][j]) return false;
    return true;
}

bool solve(int board[][10], int col, int N) {
    if (col >= N) return true;
    for (int i = 0; i < N; i++) {
        if (isSafe(board, i, col, N)) {
            board[i][col] = 1;
            if (solve(board,

 col + 1, N)) return true;
            board[i][col] = 0; // backtrack
        }
    }
    return false;
}

int main() {
    int N = 4;
    int board[10][10] = {0};
    solve(board, 0, N);
}
```
