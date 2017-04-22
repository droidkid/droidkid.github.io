---
layout: post
title: Graph Snippets
---

Notes and problems on graph algorithms.
<!--more-->

Floyd Warshall
--------------
Considering that finding the shortest path between any two points can be done in O(V<sup>2</sup>), and there are V<sup>2</sup> paths in a graph, Floyd Warshall is amazing because it can get All Pairs shortest path in O(V<sup>3</sup>). The proof is beautiful and a good introduction to dynamic programming.

````
/*
The Heart of Floyd Warshall is the dp
dp[i][j][k] = min(dp[i][j][k-1], dp[i][k][k-1] + dp[k][j][k-1];
Try using this dp for problems.
*/

for(int k=0;k<n;k++){
 for(int i=0;i<n;i++){
    for(int j=0;j<n;j++){
        int temp=graph[i][k]+graph[j][k];
        graph[i][j] = min(temp, graph[i][j]);
    }
  }
}
````
