# 1260 DFS와 BFS

[문제 링크](https://www.acmicpc.net/problem/1260)

### 내 코드
```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.*;

public class Main {
    static int n, m, v;
    static boolean[][] graph;
    static boolean[] isVistead;
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        String[] temp = br.readLine().split(" ");
        n = Integer.parseInt(temp[0]);
        m = Integer.parseInt(temp[1]);
        v = Integer.parseInt(temp[2])-1;

        graph = new boolean[n][n];
        String[] line;
        for(int i = 0; i < m; i++){
            line = br.readLine().split(" ");
            int x = Integer.parseInt(line[0])-1;
            int y = Integer.parseInt(line[1])-1;
            graph[x][y] = true;
            graph[y][x] = true;

        }

        isVistead = new boolean[n];
        Arrays.fill(isVistead, false);
        DFS(v);
        System.out.println();

        Arrays.fill(isVistead, false);
        BFS(v);
        System.out.println();
    }
    public static void DFS(int x){
        isVistead[x] = true;
        System.out.printf("%d ", x+1);
        for(int i=0; i<n; i++){
            if(graph[x][i] && !isVistead[i]){
                DFS(i);
            }
        }

    }
    public static void BFS(int x){
        Queue<Integer> stack = new LinkedList<>();
        stack.offer(x);
        isVistead[x] = true;
        while(!stack.isEmpty()){
            int now = stack.poll();
            System.out.printf("%d ", now+1);
            for(int i=0; i<n; i++) {
                if (graph[now][i] && !isVistead[i]) {
                    isVistead[i] = true;
                    stack.offer(i);
                }
            }
        }
    }
}
```

