# Recurrence Analysis -- Mystery Function
I certify that I have listed all sources used to complete this exercise, including the use of any Large Language Models. All of the work is my own, except where stated otherwise. I am aware that plagiarism carries severe penalties and that if plagiarism is suspected, charges may be filed against me without prior notice. No sources were used.
Asked Aaron Krapes to check if it seemed right, only note was that I dropped the n(T(1) before the end when it should only be dropped in the Big O notation.

Analyze the running time of the following recursive procedure as a function of
$n$ and find a tight big $O$ bound on the runtime for the function. You may
assume that each operation takes unit time. You do not need to provide a formal
proof, but you should show your work: at a minimum, show the recurrence relation
you derive for the runtime of the code, and then how you solved the recurrence
relation.

```javascript
function mystery(n) {
    if(n <= 1)            O(1)
        return;
    else {
        mystery(n / 3);   O(?)
        var count = 0;
        mystery(n / 3);   O(?)
        for(var i = 0; i < n*n; i++) {            O(n^2)
            for(var j = 0; j < n; j++) {          O(n)
                for(var k = 0; k < n*n; k++) {    O(n^2)
                    count = count + 1;
                }
            }
        }
        mystery(n / 3);   O(?)
    }
}
```

Add your answer to this markdown file. [This
page](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions)
might help with the notation for mathematical expressions.



T(n) = 1, for n <= 1;

T(n) = 3<sup>i</sup>(T(n/3) + (n<sup>2</sup>)(n)(n<sup>2</sup>)), for n >= 1;

T(n) = 3<sup>i</sup>T(n/3<sup>i</sup>) + 3<sup>i</sup>(n<sup>5</sup>)

i = log<sub>3</sub>(n)

3 <sup>log<sub>3</sub>n</sup>(T(1)) + 3<sup>log <sub>3</sub> n</sup>(n<sup>5</sup>)

3 <sup>log <sub>3</sub> n</sup> = n

n(T(1)) + n(n<sup>5</sup>)

T(n) = n(T(1)) + n<sup>6</sup>

T(n) ∈ $O$(n<sup>6</sup>)
