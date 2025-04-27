# I
![5 @)3B4 7OPOB)9)Z1@IG3H_tmb](https://github.com/user-attachments/assets/17cd19c7-cfd9-4e25-9fb4-2780a2402bd7)

# II
``` cpp


#include <iostream>
#include <vector>
#include <queue>
#include <stack>
using namespace std;

class Graph {
private:
    vector<vector<int>> adj;

public:
    Graph(int n)
            : adj(n)   
    {}

    void addEdge(int u, int v) {
        adj[u].push_back(v);  
        adj[v].push_back(u);  
    }

    void BFS(int start) {


        vector<bool> discovered(adj.size(), false);

       
        queue<int> frontier;

        
        discovered[start] = true;
        frontier.push(start);



        
        while (!frontier.empty()) {
            int u = frontier.front(); 
            frontier.pop();           
            cout << char('A' + u) << " "; 

           
            for (int v : adj[u]) {
               
                if (!discovered[v]) {
                    discovered[v] = true; 
                    frontier.push(v);     
                }
            }
        }
        cout << endl;
    }

  
    void DFS(int start) {

        vector<bool> visited(adj.size(), false);


        stack<int> st;


        st.push(start);



        while (!st.empty()) {
            int u = st.top(); 
            st.pop();         

            if (!visited[u]) {
                visited[u] = true;            
                cout << char('A' + u) << " "; 



                for (auto it = adj[u].rbegin(); it != adj[u].rend(); ++it) {
                    int v = *it;
                    if (!visited[v]) {
                        st.push(v); 
                    }
                }
            }
        }
        cout << endl;
    }
};

int main() {

    Graph G(6);

    // A = 0 ， F = 5

    G.addEdge(0, 1); // A–B
    G.addEdge(0, 3); // A–D
    G.addEdge(1, 4); // B–E
    G.addEdge(1, 5); // B–F
    G.addEdge(4, 5); // E–F
    G.addEdge(5, 2); // F–C

    // Start with A for both 
    G.BFS(0);
    G.DFS(0);

    return 0;
}
```

