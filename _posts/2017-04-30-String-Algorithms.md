---
layout: post
title: String Algorithms
---

Notes and problems on String algorithms (KMP, Rabin Karp, largest palindrome)
<!--more-->

String algorithms
===============

KMP
----

```
string pattern;
string text;

// prefix[i] - Length of largest equal prefix & suffix of substring(0, i-1)
// Should be atleast pattern.size() + 1 (since we are using 1 based index)
int prefix[LIM];

// Should be atleast text.size()
int kmp_mark[LIM];

void buildPrefix(){
    prefix[0] = 0;
    prefix[1] = 0;
    int n = pattern.size();
    for(int i=2; i<=n; i++){
        int j = prefix[i-1];
        char c = pattern[i-1];
        while(true){
            if(c==pattern[j]){
                prefix[i] = j+1;
                break;
            }
            if(j==0){
                prefix[i] = 0;
                break;
            }
            j = prefix[j];
        }
    }
}

void kmp_mark_text(){
    int len = text.size();
    int j = 0;
    int i = 0;
    while(i<len){
        if(text[i]==pattern[j]){
            if(j==pattern.size()-1){
                mark[i] = 1; // substring ending here is equal to pattern
            }
            j++;
            i++;
            continue;
        }
        if(j==0){
            i++;
            continue;
        }
        j = F[j];
    }
}
```

Good Resources/Problems on KMP:

* [Topcoder](https://www.topcoder.com/community/data-science/data-science-tutorials/introduction-to-string-searching-algorithms/)
* TODO: Add links to good KMP problems. There were a few on codeforces.
