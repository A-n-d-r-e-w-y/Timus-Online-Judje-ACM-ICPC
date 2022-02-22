#include <stdio.h>
#include <vector>
#include <queue>

struct vertex
{
    std::vector<vertex*> out;
    int n;
};

void explore(vertex* u, std::vector<vertex*>& ans)
{   // Go as far as we can in some direction and queue up all nodes. We are guaranteed to return.
    ans.push_back(u);
    std::queue<vertex*> q;
    vertex* v = u;
    while(!v->out.empty())
    {   // I wish pop_back returned a value
        auto w = v->out.back();
        v->out.pop_back();
        v = w;
        q.push(v);
    }
    while(!q.empty())
    {   // For all queued nodes, recurse
        explore(q.front(), ans);
        q.pop();
    }
}

int main()
{
    int n;
    std::vector<vertex> v(10001); // Node storage

    scanf("%d", &n);
    int m, last, tot = 0;

    for(int i = 0; i < n; i++)
    {
        scanf("%d", &m);
        scanf("%d", &last);
        for(int j = 1; j <= m; j++)
        {
            int u;
            scanf("%d", &u);
            v[u].n = u;
            v[last].out.push_back(&v[u]);
            last = u;
        }
    }
    std::vector<vertex*> ans;
    explore(&v[last], ans);
    printf("%d ", ans.size()-1);
    for(auto it = ans.begin(); it < ans.end(); it++)
        printf("%d ", (*it)->n);
    return 0;
}