We use the integers _a_, _b_, and _n_ to create the following series:

```math
(a + 2^0.b),(a + 2^0.b + 2^1.b),... ..., (a + 2^0.b + 2^1.b+...+2^{n-1} . b)
```

You are given _q_ queries in the form of _a_, _b_, and _n_. For each query, print the series corresponding to the given _a_, _b_, and _n_ values as a single line of _n_ space-separated integers.

## Input Format

The first line contains an integer, _q_, denoting the number of queries.
Each line _i_ of the _q_ subsequent lines contains three space-separated integers describing the respective $a_i$, $b_i$, and $n_i$ values for that query.

## Constraints

<ul>
<li> 0 &leq; q &leq; 500 </li>
<li> 0 &leq; a,b &leq; 50 </li>
<li> 1 &leq; n &leq; 15 </li>
</ul>

## Output Format

For each query, print the corresponding series on a new line. Each series must be printed in order as a single line of _n_ space-separated integers.

Sample Input
```js
2
0 2 10
5 3 5
```
Sample Output
```js
2 6 14 30 62 126 254 510 1022 2046
8 14 26 50 98
```
Explanation

We have two queries:

1. We use _a_=0, _b_=2, and _n_=10 to produce some series $s_0$, $s_1$, ... ..., $s_{n-1} $ :

    * $s_o = 0 + 1*2 = 2$

    * $s_1 = 0 + 1*2 + 2*2 = 6$

    * $s_2 = 0 + 1*2 + 2*2 + 4*2 = 14$

    ... and so on.

    Once we hit _n_ = 10, we print the first ten terms as a single line of space-separated integers.

2. We use _a_=5, _b_=3, and _n_=5 to produce some series $s_0$, $s_1$, ... ..., $s_{n-1} $ :

    * $s_o = 5 + 1*3 = 8$

    * $s_1 = 5 + 1*3 + 2*3 = 14$

    * $s_2 = 5 + 1*3 + 2*3 + 4*3 = 26$

    * $s_2 = 5 + 1*3 + 2*3 + 4*3 + 8*3 = 50$

    * $s_2 = 5 + 1*3 + 2*3 + 4*3 + 8*3 + 16*3 = 98$


We then print each element of our series as a single line of space-separated values.

# Solution

```java
import java.util.*;
import java.io.*;

class Solution{
    public static void main(String []argh){
        Scanner in = new Scanner(System.in);
        int t=in.nextInt();
        for(int i=0;i<t;i++){
            int a = in.nextInt();
            int b = in.nextInt();
            int n = in.nextInt();
            
            for (int term = 0; term < n ; term++){
                        //System.out.println("term : "+term);
                        double res = (a+mathFunct(n, term, b));
                        System.out.print(Math.round(res)+"\t");
                    }
                    System.out.print("\n");
        }
        in.close();
    }
    
    public static double mathFunct(int n, int power, int b ){
        double eqRes = 0;
        for(int p=0; p <= power; p++){
            //System.out.println(">> p : "+p);
            eqRes += Math.pow(2, p)*b;
        }
        
        return eqRes;
    }
}
```
