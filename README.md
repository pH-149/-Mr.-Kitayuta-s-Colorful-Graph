# -Mr.-Kitayuta-s-Colorful-Graph
graph
<br>
def dfs(u, v, vis, graph):
    if u == v:
        return True
    vis[u] = True
    for neighbour in graph[u]:
        if not vis[neighbour]:
            if dfs(neighbour, v, vis, graph):
                return True
    return False


def kitayu():
    n, m = map(int, input().split())
    edges = []

    for _ in range(m):
        a, b, c = map(int, input().split())
        edges.append((a, b, c))

    q = int(input())
    quer = []
    for _ in range(q):
        u, v = map(int, input().split())
        quer.append((u, v))

    # Process each query
    for u, v in quer:
        cnt = 0
        for color in range(1, m + 1):
            graph = [[] for _ in range(n + 1)]  


            for a, b, c in edges:
                if c == color:
                    graph[a].append(b)
                    graph[b].append(a)

            vis = [False] * (n + 1)
            if dfs(u, v, vis, graph):
                cnt += 1

        print(cnt)


kitayu()
