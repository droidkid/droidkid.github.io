---
layout: post
title: Data Structures
---

Notes and problems on DataStructures (Tries, BIT, DSU)
<!--more-->

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
