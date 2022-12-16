# Design Principles

## **Things to consider while coding:**

1. Extensible
2. Targeted
3. Non redundant
4. Testable
5. Minimal external dependencies

## **Things to consider before naming things in code:**

1. Short but unambiguous ( eq. sqrt instead of square\_root )
2. Choose verbose over ambiguous ( eg. sqrt\_addition\_result instead resaddsqrt )
3. Avoid using type in name ( eg. names instead of name\_list )
4. &#x20;Use abbreviations if they are well known and are not ambiguous in current context ( eg. ts instead of timestamp is ok )
5. **Classes are Nouns ( as they represent objects ) their methods are Verbs their attributes can be nouns, adjectives or adverbs.**

## Things to consider while writing methods / functions:

1. Single responsibility (eg. dont mutate and filter result in the same function)
2. Avoid side effects (ie. Dont mutate out of scope variables unless the function / method explicitly intends to do this )
3. Dont abstract too much in a single function
4. A function shouldnt occupy more than 3/4 of ur screen in worst case (considering your screen shows 40 lines). Ideally it should be 2 functions or more per screen.
5. Dont take many params, it usually indicates that we can split function.

* **Split, reduce abstraction in single call is what we do to resolve function issues.**

## Things to Consider while commenting:

1. Code should speak for itself mostly.
2. Some business logic or something complex ( eg. a complex regex ) can go as comment.
3. Dont add repetitive or overly verbose comments.&#x20;
4. Dont comment out code, delete it if its not needed, if u need it get it from the version control thats what VCS is for.

## Things to consider while writing modules:

1. Single responsibility
2. its ideal ( but not practical ) to have one class per module
3. Modules shouldnt exceed 300-400 LOC

## Quality Metrics

1. Cyclomatic complexity
2. Linter checks for language standards ( eg. TSLint, PyLint )
3. Code Coverage
4. Duplicate Code Percentage
5. High Cohesion and Low Coupling

****

