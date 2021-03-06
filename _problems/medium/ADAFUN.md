---
category_name: medium
problem_code: ADAFUN
problem_name: 'Ada Function'
languages_supported:
    - C
    - CPP14
    - JAVA
    - PYTH
    - 'PYTH 3.6'
    - PYPY
    - CS2
    - 'PAS fpc'
    - 'PAS gpc'
    - RUBY
    - PHP
    - GO
    - NODEJS
    - HASK
    - rust
    - SCALA
    - swift
    - D
    - PERL
    - FORT
    - WSPC
    - ADA
    - CAML
    - ICK
    - BF
    - ASM
    - CLPS
    - PRLG
    - ICON
    - 'SCM qobi'
    - PIKE
    - ST
    - NICE
    - LUA
    - BASH
    - NEM
    - 'LISP sbcl'
    - 'LISP clisp'
    - 'SCM guile'
    - JS
    - ERL
    - TCL
    - kotlin
    - PERL6
    - TEXT
    - 'SCM chicken'
    - PYP3
    - CLOJ
    - COB
    - FS
max_timelimit: '3'
source_sizelimit: '50000'
problem_author: alei
problem_tester: null
date_added: 17-10-2018
tags:
    - alei
    - dfs
    - dynamic
    - hard
    - tries
editorial_url: 'https://discuss.codechef.com/problems/ADAFUN'
time:
    view_start_date: 1548009002
    submit_start_date: 1548009002
    visible_start_date: 1548009002
    end_date: 1735669800
    current: 1559472966
is_direct_submittable: false
layout: problem
---
All submissions for this problem are available.\###Read problems statements in \[Hindi\](http://www.codechef.com/download/translated/COOK102/hindi/ADAFUN.pdf), \[Mandarin Chinese\](http://www.codechef.com/download/translated/COOK102/mandarin/ADAFUN.pdf), \[Russian\](http://www.codechef.com/download/translated/COOK102/russian/ADAFUN.pdf), \[Vietnamese\](http://www.codechef.com/download/translated/COOK102/vietnamese/ADAFUN.pdf) and \[Bengali\](http://www.codechef.com/download/translated/COOK102/bengali/ADAFUN.pdf) as well. Ada has a set of $N$ non-negative integers $S = \\{x\_1, x\_2, \\ldots, x\_N\\}$. She defined the function $W$ as follows: - $W(\\{\\}) = 0$. - If $S = \\{a\\}$, then $W(S) = a$. - If $S = \\{a, b\\}$ (so $|S| = 2$), then $W(S) = (a \\oplus b) - 1$. - If $|S| \\ge 3$, then to calculate $W(S)$, find any two elements of $S$ that are congruent (have the same remainders) modulo the highest possible power of $2$ (the highest power for which such a pair exists). Let's denote them by $a$ and $b$. Then $W(S) = W(\\{a, b\\}) \\oplus W(S \\setminus \\{a, b\\})$. - It is guaranteed that $W(S)$ is well-defined, i.e. does not depend on the exact choice of the two congruent elements. Here, $\\oplus$ represents the binary XOR operation and $A \\setminus B$ represents set difference. Ada needs to calculate the function $W$ for each set that is created by removing exactly one element from $S$. Formally, she wants to find $W(S \\setminus \\{x\_i\\})$ for each valid $i$. Can you help her? ### Input - The first line of the input contains a single integer $T$ denoting the number of test cases. The description of $T$ test cases follows. - The first line of each test case contains a single integer $N$. - The next line contains $N$ space-separated integers $x\_1, x\_2, \\ldots, x\_N$. ### Output For each test case, print a single line containing $N$ space-separated integers. For each valid $i$, the $i$-th of these integers should denote $W(S \\setminus \\{x\_i\\})$. ### Constraints - $1 \\le T \\le 10^6$ - $1 \\le N \\le 10^5$ - $0 \\le x\_i \\le 10^{18}$ for each valid $i$ - $x\_1, x\_2, \\ldots, x\_N$ are pairwise distinct - the sum of $N$ over all test cases does not exceed $10^6$ ### Example Input ``` 1 6 0 1 2 5 7 8 ``` ### Example Output ``` 13 4 3 0 6 5 ```
