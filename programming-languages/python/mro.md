# MRO

Method resolution order.

Done using C3 Linearization.

### C3 Linearization

L(Z) = Z + merge( L(0), L(1)..... L(n), \[0, 1, ... n] )

merge(0, 1, ... n ) = recursively pick a head from any list thats not in any other list's tail.

L(\[A, B], \[A, B, C], \[A, B, C, D])\
\=> A + L(\[B], \[B, C], \[B, C, D])\
\=> A, B + L(\[C], \[C, D])\
\=> A, B, C + L(\[D])\
\=> A, B, C, D \


If multiple heads are valid pick the left most.

{% embed url="https://en.wikipedia.org/wiki/C3_linearization" %}
