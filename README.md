[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-24ddc0f5d75046c5622901739e7c5dd533143b0c8e959d652212380cedb1ea36.svg)](https://classroom.github.com/a/OlW38W4k)
# Recurrence Analysis -- Mystery Function

Analyze the running time of the following recursive procedure as a function of
$n$ and find a tight big $O$ bound on the runtime for the function. You may
assume that each operation takes unit time. You do not need to provide a formal
proof, but you should show your work: at a minimum, show the recurrence relation
you derive for the runtime of the code, and then how you solved the recurrence
relation.

```javascript
function mystery(n) {
    if(n <= 1)
        return;
    else {
        mystery(n / 3);
        var count = 0;
        mystery(n / 3);
        for(var i = 0; i < n*n; i++) {
            for(var j = 0; j < n; j++) {
                for(var k = 0; k < n*n; k++) {
                    count = count + 1;
                }
            }
        }
        mystery(n / 3);
    }
}
```

Add your answer to this markdown file. [This
page](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions)
might help with the notation for mathematical expressions.

// Worked with Jacob Johnson

$$ T(n) =
   \begin{cases}
       1 & n \leq 1\\
       3T(\frac{n}{3}) + n^5 & n > 1
   \end{cases}
$$

$T(n) = 3T(\frac{n}{3}) + n^5 $

$= 3(3T(\frac{n}{9}) + \frac{n^5}{3^5}) + n^5$

$= 9T(\frac{n}{9}) + \frac{n^5}{3^4} + n^5$

$= 27T(\frac{n}{27}) + \frac{n^5}{9^4} + \frac{n^5}{3^4} + n^5$

// in terms of 3

$= 27T(\frac{n}{27}) + \frac{n^5}{3^8} + \frac{n^5}{3^4} + n^5$

$…$

$= 3^iT(\frac{n}{3^i}) +$
$\sum_{k=0}^i (\frac{1}{3^4})^k$
$\cdot n^5 $

// I am aware that the i in the sum is not displaying properly in math notation, it seems to be an issue with github

// https://github.com/orgs/community/discussions/17051

for $i = \log n$

$=  nT(1) + n^6 \in \Theta(n^6)$
