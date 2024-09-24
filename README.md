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

```math

T(n) = 1, for n <= 1;
T(n) = 3<sup>i</sup> (T(n/3) + n<sup>2</sup> * n * n<sup>2</sup>), for n >= 1;

T(n) = 3<sup>i</sup> * T(n/3<sup>i</sup>) + 3<sup>i</sup> * n<sup>5</sup>

i = log<sub>3</sub>(n)

3^log<sub>3</sub>(n) * T(1) + 3^log<sub>3</sub>(n) * n^5

3^log<sub>3</sub>(n) = n

n * T(1) + n * n<sup>5</sup>

big theta (nT(1) + n<sup>6</sup>)
```
