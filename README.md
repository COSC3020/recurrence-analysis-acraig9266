# Recurrence Analysis -- Mystery Function
I certify that I have listed all sources used to complete this exercise, including the use of any Large Language Models. All of the work is my own, except where stated otherwise. I am aware that plagiarism carries severe penalties and that if plagiarism is suspected, charges may be filed against me without prior notice.
Asked Aaron Krapes to double check for me. ChatGPT was used to nicely format the math for markdown

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
        mystery(n / 3);                           n/3
        var count = 0;                            O(1)
        mystery(n / 3);                           n/3
        for(var i = 0; i < n*n; i++) {            n^2
            for(var j = 0; j < n; j++) {          n
                for(var k = 0; k < n*n; k++) {    n^2
                    count = count + 1;            O(1)
                }
            }
        }
        mystery(n / 3);                           n/3
    }
}
```

Add your answer to this markdown file. [This
page](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions)
might help with the notation for mathematical expressions.



$$
T(n) = 
\begin{cases} 
1 & \text{for } n \leq 1 \\ 
3\left(T\left(\frac{n}{3}\right) + n^{5}\right) & \text{for } n > 1 
\end{cases}
$$

$$ T(n) = 3\left(T\left(\frac{n}{3}\right) + n^{5}\right) $$

$$ T(n) = 3\left(3\left(T\left(\frac{n}{9}\right) + n^{5}\right) + n^{5}\right)$$

$$ T(n) = 9\left(T\left(\frac{n}{9}\right) + n^{5}\right) + 3n^{5} $$

$$ T(n) = 3\left(9\left(T\left(\frac{n}{9}\right) + n^{5} \right) + n^{5}\right) + 3n^{5} $$

$$ T(n) = 27\left(T\left(\frac{n}{27}\right) + n^{5}\right) + 6n^{5} $$

$$ T(n) = 27T\left(\frac{n}{27}\right) + 27n^{5} + 6n^{5} $$

$$ T(n) = 3^{i}T\left(\frac{n}{3^{i}}\right) + 3^{i}n^{5} + 2in^{5} \quad \text{for } i = \lg(n) $$

$$ 3^{\lg(n)} = n $$

$$ = nT\left(\frac{n}{n}\right) + n(n^{5}) + \lg(n)n^{5} $$

$$ = nT(1) + n(n^{5}) + \lg(n)n^{5} $$

$$ = n + n^{6} + \lg(n)n^{5} $$

$$ T(n) \in \Theta(n^{6}) $$


