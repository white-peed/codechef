---
category_name: challenge
problem_code: EMBED
problem_name: Embedding
languages_supported:
    - C
    - CPP14
    - JAVA
    - PYTH
    - 'PYTH 3.5'
    - CS2
    - 'PAS fpc'
    - 'PAS gpc'
    - RUBY
    - PHP
    - GO
    - NODEJS
    - HASK
    - SCALA
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
    - PERL6
    - TEXT
    - CLOJ
    - FS
max_timelimit: '5'
source_sizelimit: '50000'
problem_author: nssprogrammer
problem_tester: laycurse
date_added: 29-11-2014
tags:
    - challenge
    - march15
    - nssprogrammer
editorial_url: 'http://discuss.codechef.com/problems/EMBED'
time:
    view_start_date: 1426498200
    submit_start_date: 1426498200
    visible_start_date: 1426498200
    end_date: 1735669800
    current: 1525199662
is_direct_submittable: false
layout: problem
---
All submissions for this problem are available.###  Read problems statements in [Mandarin Chinese](http://www.codechef.com/download/translated/MARCH15/mandarin/EMBED.pdf) and [Russian](http://www.codechef.com/download/translated/MARCH15/russian/EMBED.pdf).

You have **N** points, numbered from **1** to **N**. You have to position these **N** points on the Cartesian plane.

You have to decide the coordinates of the points. But there are some restrictions. Firstly, the coordinates should be integers, at least **1** and at most **4000**, thus you can put a point only on a lattice point. Secondly, every point must have distinct coordinates.

After the points are positioned on the Cartesian plane, they need to be connected through line segments. The length of a line segment connecting two points is of course the euclidean distance between the points. There will be **N − 1** line segments in total. The structure of points and line segments will be the same as tree in graph theory. Every pair of points will be connected directly or indirectly by the segments.

There is one more restriction corresponding to the length of each line segment. Let the **i**th segment connect points **Pi** and **Qi**. You are given the minimum length **Ki** and the maximum length **Li** of the **i**th segment, receptively , the length between points **Pi** and **Qi** must be at least **Ki** and at most **Li**.

**What needs to be optimized ?**

Here we explain what needs to be optimized. Two points are considered to be adjacent if they are connected through a line segment. You want to minimize the ratio between the maximum distance between any two adjacent points and the minimum distance between any two non-adjacent points over all the points on the Cartesian plane. Also there are some **evil coordinates** on the Cartesian plane. You will be given three integers **A**, **B** and **S**. Then, the coordinates **(x, y)** are evil coordinates if and only if **(Ax mod 10007) + (By mod 10007) ≤ S**. Assignment of evil coordinates to any point shall be avoided so far as possible. In addition, it is better that each segment does not intersect with other segments (please see Scoring section for definition of "intersect").

Your task is to find valid and better integer coordinates for each point on the Cartesian plane. Of course, it is too hard to find the optimal solution. Thus your final aim is to maximize your total score described in the below Scoring section.

### Input

The first line of input contains an integer **T**, denoting the number of test cases. Then **T** test case follow.

The first line of each test case contains an integer **N**, denoting the number of the points. The second line contains three integers **A**, **B** and **S**, denoting the information about evil cells. Then **N − 1** lines follow. The **i**th of such lines contains four space-separated integers **Pi**, **Qi**, **Ki** and **Li**, denoting the information about the **i**th segment.

### Output

For each test case, print **N** lines, where the **i**th line should have two space-separated integers **xi** and **yi**, denoting the coordinates of point **i**.

### Constraints

- **1 ≤ T ≤ 100**
- **3 ≤ N ≤ 500**
- **1 ≤ A, B ≤ 10006**
- **0 ≤ S ≤ 20012**
- **1 ≤ Pi, Qi ≤ N**, and **Pi ≠ Qi**
- **1 ≤ Ki ≤ Li ≤ 6000**
- The structure of the graph denoted by input will be a tree
- All the judge file (not included the below Example) generated by the method described in Test generation section

### Example

<pre>
<b>Input:</b>
3
4
6476 5351 10367
1 2 1 5
2 3 1 5
3 4 1 5
4
8316 8371 7
1 2 100 5000
2 3 100 5000
3 4 100 5000
4
8316 8371 7
1 2 100 5000
2 3 100 5000
3 4 100 5000

<b>Output:</b>
1 1
2 1
2 2
3 2
1000 1000
1000 2000
1000 1100
1000 1900
1000 1000
1000 1200
1000 1500
1000 2000
</pre>### Test generation

We have **10** input files. Each of our input file contains **100** test cases, that is, **T = 100**. Each test case is generated as follows.

At first, the integer **N** is chosen from **\[3, 500\]**, randomly and uniformly. Then the integer **A** and **B** are chosen from **\[1, 10006\]**, randomly, uniformly and independently. The integer **S** is also chosen from **\[0, 20012\]**, randomly and uniformly.

Then we enumerate the lattice points which are not evil points, let the set **e** be the such lattice points. If the number of elements of the set **e** is less than **2 × N**, then the test is discarded, and new a test case is generated instead of it. For **i = 1, 2, ..., N**, one point, say **fi** are chosen from the set **e** randomly and uniformly, and delete **fi** from the set **e**. Thus we selected **N** distinct lattice points **fi** which are not evil.

Then the real parameter **r** are chosen from the set **{0.6, 0.8, 0.9, 1.0, 1.1, 1.3, 1.6}** randomly and uniformly. For **i = 2, 3, ..., N**, we choose **j** from **\[1, i−1\]**, randomly but not uniformly. Here, let **sum = r1 + r2 + ... + ri−1**, then the probability of **j = k** is **rk / sum**. This means that there is a segment between the points **i** and **j**.

The minimum length and maximum length of each segment are generated as follows. Let the segment connect points **i** and **j**, and let the length between **fi** and **fj** be **d**. The real value **a** is chosen from **\[d/5, d\]**, and the real value **b** are chosen from **\[d, 5×d\]** randomly, uniformly and independently, then the minimum length of the segment is set as **max(1, floor(a))**, and the maximum length of the segment is set as **min(6000, ceil(b))**.

Lastly, the numbers of points are shuffled, and the order of edges are also shuffled, where every permutation occurs with the same probability. And, for each **i**, **Pi** and **Qi** are swapped with probability **0.5**.

### Scoring

At first, you will get _Wrong Answer_ if you print invalid coordinates for at least one test case.

The score for each test case are calculated as follows. Let **X** be the maximum distance between any two adjacent points over the set of points, and **Y** be the minimum distance between any two non-adjacent points over the set of points, And let **C** be the number of the unordered pairs **(u, v)** of segments, where the **u**th segment intersects with the **v**th segment. And let **W** be the number of the points on the evil coordinate. Then the score for this case is calculated as : 

**Score = 10000 × Y / X × (1 − Z) × (1 − Q),**
where **Z = 2 × C / (N − 1) / (N − 2),**
and **Q = W / N**.

 Here the **u**thline segment intersects the **v**thline segment if and only if there is some point **p** such that:

- **p** is not an end point of the **u**th segment, or **p** is not an end point of the **v**th segment
- **p** is on both the **u**th segment and **v**th segment, where the segment include the end points.

Then the score for each test file is defined by the sum of the score of test cases in the test file. Finally, the final score is defined by the average of the score for each test file.

During the contest, the shown score will be affected by only the first **20** test case for each test file. That is, the score of the last **80** test cases are calculated as 0.

### Explanation

**Example 1.**

The above output is a valid one. Let's check it. All points have distinct integer coordinates. And the length of the **1**st segment is **sqrt( (x1 − x2)2 + (y1 − y2)2 ) = sqrt( (1 − 2)2 + (1 − 1)2 ) = 1**. The minimum length and maximum length of the **1**st segment are **1** and **5** respectively, so it does not break constraints. Similarly, the length of the **2**nd segment and the **3**rd segment are **1** and **1** respectively. They also do not break the constraint. So the output is valid.

Then let's calculate the score for this test case. The pairs of adjacent points are **(1, 2)**, **(2, 3)** and **(3, 4)**. The all distances of the between adjacent points are **1**, as seeing above. Thus **X = 1**, denoting the maximum distance between any two adjacent points over the set of points.

The pairs of non-adjacent points are **(1, 3)**, **(1, 4)** and **(2, 4)**. The distances between non-adjacent points are **1.414...**, **2.236...** and **1.141...** respectively. Thus **Y = 1.414...**, denoting the the minimum distance between any two non-adjacent points over the set of points.

You can see that each segment does not intersect with others. Thus **C = 0**.

The only point **4** on an evil coordinate, since

- About point **1**: **(Ax1 mod 10007) + (By1 mod 10007) = (64761 mod 10007) + (53511 mod 10007) = 11827 > S**,
- About point **2**: **(Ax2 mod 10007) + (By2 mod 10007) = (64762 mod 10007) + (53511 mod 10007) = 14597 > S**,
- About point **3**: **(Ax3 mod 10007) + (By3 mod 10007) = (64762 mod 10007) + (53512 mod 10007) = 12420 > S**,
- About point **4**: **(Ax4 mod 10007) + (By4 mod 10007) = (64763 mod 10007) + (53512 mod 10007) = 8389 ≤ S**.

Thus **W = 1**.

Put it all together, the score of this test case is about **10000 × 1.414... / 1 × (1 − 0) × (1 − 0.25) = 10606.6017....**

**Example 2.**

You can check that the output is valid. But it is also can be checked easily, each segment intersects all other segments. Thus **C = 3 × 2 / 2 = 3**, and **Z = 1**. Then the score of this test case is 0.

**Example 3.**

You can check that the output is valid. And, in this case, each segment does not intersect all other segments. Please note that, in the definition of intersect, the point **p** is not an end point of at least one segment. In this case, **X = Y = 500, C = 0, W = 0**. Thus the score is just **10000**.