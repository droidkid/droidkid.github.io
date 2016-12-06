---
layout: post
title: Coding Competition Notes & Snippets
---

A bunch of notes and snippets about data structures and algorithms. Mostly for me to copy paste in competitions :P
<!--more-->
Graphs
======

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


Data Structures
===============

Trie
----

A trie is a kind of search tree. Elements can be searched by their prefixes. Walking from the root gives prefixes of the words present in the tree. Generally nodes are marked if they are the end of a word.

Here is some sample C++ code for a trie to store words having 26 different types of characters.
```
struct trie{
    trie *next[26];
    trie(){
       for(int i=0; i<26; i++){
            next[i] = NULL;
        }
    }
    void insertWord(string s){
        trie *t = this;
        int sz = s.size();
        for(int i=0; i<sz; i++){
            int c = s[i]-'a';
            if( t->next[c] == NULL){
                t->next[c] = new trie;
            }
            t = t->next[c];
        }
    }

} start;
```

Good Resources/Problems on Tries:
* [Topcoder](https://www.topcoder.com/community/data-science/data-science-tutorials/using-tries/), has a few problems also
* [Threads @ III-Hyderabad](https://threads-iiith.quora.com/Tutorial-on-Trie-and-example-problems)
* [Polo the Penguin and the XOR](https://www.codechef.com/problems/PPXOR)
