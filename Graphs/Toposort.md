## Topological sorting
Exists only for [DAG(Directed Acyclic Graph)](https://www.geeksforgeeks.org/dsa/introduction-to-directed-acyclic-graph/).
Application:
* Helps in scheduling tasks or events based on dependencies.
* Detects cycles in a directed graph.
* Efficient for solving problems with precedence constraints.

```cpp
	void dfs(int node, int vis[], stack<int> &st,
	         vector<int> adj[]) {
		vis[node] = 1;
		for (auto it : adj[node]) {
			if (!vis[it]) dfs(it, vis, st, adj);
		}
		st.push(node);
	}
vector<int> topoSort(int V, vector<int> adj[])
	{
		int vis[V] = {0};
		stack<int> st;
		for (int i = 0; i < V; i++) {
			if (!vis[i]) {
				dfs(i, vis, st, adj);
			}
		}

		vector<int> ans;
		while (!st.empty()) {
			ans.push_back(st.top());
			st.pop();
		}
		return ans;
	}
```
>Tc:O(N+E)+O(N)

>Sc:O(2N)
