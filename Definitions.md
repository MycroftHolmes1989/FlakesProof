## FileContent:
FileContent is defined as a data structure that can be expressed as a finite array of integers. The length of the FileContent is defined as the number of elements in the array.

A FileContent $F_0$ of length n can be expressed as $[a_0, a_1, a_2, ..., a_n]$ where $\forall 0 < i < n, i \in \mathbb{N}: a_i \in \mathbb{N}$.

A blank FileContent, therefore is a FileContent of zero length, and is expressed as [ ].

___
## Differential:
Differential is a data structure that stores the difference between two FileContents. Structurally, Differential is a tuple: `[sizeDiff, DiffMap]`. `sizeDiff` signifies the difference in lengths of minuend and subtrahend. DiffMap stores the difference in the content of the FileContents.

### DiffMap:
As mentioned earlier, DiffMap stores the difference in the content between the FileContents. DiffMap is implemented as a Map and it maps an integer to an integer.
`Diffmap : Int -> Int`
We will use the usual data structure terminology to talk about key and value when it comes to Map, where `Map : Key -> Value`.


### Calculation of Differentials:

Suppose we have two FileContents : $F_a$ and $F_b$. 
Let us further assume $F_a = [a_0, a_1, a_2, ..., a_i]$ and $F_b = [b_0, b_1, b_2, ..., b_j]$

The difference in the length of $F_a$ and $F_b$ will be $i - j$.
Thus if $D_{ab} = F_a - F_b$, then $D_{ab}.sizeDiff = i - j$

$D_{ab}.DiffMap$ is calculated like so:

$\forall 0 < x < min(i, j) : D_{ab}.DiffMap[x] = a_x - b_x$

For the sake of conserving space, we do not store values in Diffmap where $a_x - b_x = 0$.
