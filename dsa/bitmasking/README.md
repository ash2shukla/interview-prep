# Bitmasking

Instead of storing unique items in a set, store them in an integer.

If "apple", "orange", "pineapple" could correspond to index 0, 1, 2\
\
Then "apple", "orange" could be stored in a 8 bit integer as 00000011\
Then "apple", "pineapple" could be stored in a 8 bit integer as 00000101

**Setting n-th bit: num = num | 1 << bit**\
**Intersections:  A\&B**\
**Union: A|B**\
**Difference: A & \~(A\&B)** (Elements in A that are not in B )
