# [알고리즘] 프림 알고리즘 (Prim's algorithm)

## 프림 알고리즘

- 하나의 정점에서 연결된 간선들 중에 하나씩 선택하면서 MST를 만들어가는 방식 
    1.  임의 정점을 하나 선택해서 시작
    2.  선택한 정점과 인접하는 정점들 중 최소 비용의 간선이 존재하는 정점 선택
    3.  모든 정점이 선택될 때까지 1, 2번 과정 반복

## 구현 - 배열 이용

```java
import java.util.Arrays;

public class Prim {

    static final int N = 8;

    public static void main(String[] args) {
        int[][] graph = {
                {0, 0, 0, 0, 0, 0, 0, 0, 0,},
                {0, 0, 5, 0, 0, 0, 0, 0, 0,},
                {0, 5, 0, 2, 1, 0, 11, 0, 0,},
                {0, 0, 2, 0, 2, 9, 0, 0, 0,},
                {0, 0, 1, 2, 0, 3, 10, 8, 0,},
                {0, 0, 0, 9, 3, 0, 5, 0, 0,},
                {0, 0, 0, 0, 10, 5, 0, 0, 0,},
                {0, 0, 11, 0, 8, 0, 0, 0, 13,},
                {0, 0, 0, 0, 0, 0, 0, 13, 0,},
        };

        System.out.println(prim(graph));
    }

    static int prim(int[][] graph) {
        int[] minDist = new int[N + 1];
        Arrays.fill(minDist, Integer.MAX_VALUE);
        minDist[1] = 0;
        boolean[] visited = new boolean[N + 1];

        for (int i = 1; i <= N; i++) {
            int node = -1;
            int min = Integer.MAX_VALUE;
            for (int j = 1; j <= N; j++) {
                if (!visited[j] && minDist[j] < min) {
                    min = minDist[j];
                    node = j;
                }
            }
            if (node == -1) {
                break;
            }
            visited[node]=true;

            for (int j = 1; j <= N; j++) {
                if (graph[node][j] != 0 && !visited[j] && graph[node][j] < minDist[j]) {
                    minDist[j] = graph[node][j];
                }
            }
        }

        int result = 0;
        for (int j = 1; j <= N; j++) {
            result += minDist[j];
        }
        return result;
    }
}
```

## 구현 - 우선 순위 큐 이용

```java
import java.util.PriorityQueue;

public class Prim {

    static final int N = 8;

    public static void main(String[] args) {
        int[][] graph = {
                {0, 0, 0, 0, 0, 0, 0, 0, 0,},
                {0, 0, 5, 0, 0, 0, 0, 0, 0,},
                {0, 5, 0, 2, 1, 0, 11, 0, 0,},
                {0, 0, 2, 0, 2, 9, 0, 0, 0,},
                {0, 0, 1, 2, 0, 3, 10, 8, 0,},
                {0, 0, 0, 9, 3, 0, 5, 0, 0,},
                {0, 0, 0, 0, 10, 5, 0, 0, 0,},
                {0, 0, 11, 0, 8, 0, 0, 0, 13,},
                {0, 0, 0, 0, 0, 0, 0, 13, 0,},
        };

        System.out.println(primWithPQ(graph));
    }

    static int primWithPQ(int[][] graph) {
        int result = 0;

        PriorityQueue<Edge> pq = new PriorityQueue<>();
        pq.add(new Edge(1, 1, 0));

        boolean[] visited = new boolean[N + 1];

        for (int i = 1; i <= N; i++) {
            Edge edge = null;
            while (!pq.isEmpty()) {
                edge = pq.poll();
                if (!visited[edge.to]) {
                    break;
                }
            }

            if (edge == null) {
                break;
            }

            visited[edge.to] = true;
            result += edge.weight;
            for (int j = 1; j <= N; j++) {
                if (graph[edge.to][j] != 0 && !visited[j]) {
                    pq.add(new Edge(edge.to, j, graph[edge.to][j]));
                }
            }
        }
        return result;
    }

    static class Edge implements Comparable<Edge> {
        int from;
        int to;
        int weight;

        public Edge(int from, int to, int weight) {
            this.from = from;
            this.to = to;
            this.weight = weight;
        }

        @Override
        public int compareTo(Edge o) {
            return Integer.compare(weight, o.weight);
        }
    }
}
```