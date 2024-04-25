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
    // Base case: if n is less than or equal to 1, return
    if (n <= 1)
        return;
    else {
        // Recursive call to function with n divided by 3
        
        mystery(n / 3);

        // Initialize count variable
        var count = 0;

        // Another recursive call to mystery function with n divided by 3
        
        mystery(n / 3);

        // Nested loop structure
        // The outer loop runs n^2 times
        for (var i = 0; i < n * n; i++) {
            // The middle loop runs n times
            for (var j = 0; j < n; j++) {
                // The inner loop runs n^2 times
                
                for (var k = 0; k < n * n; k++) {
                    
                    count = count + 1;
                }
            }
        }

        
        mystery(n / 3);
    }
}
```
The function makes three recursive calls to itself with the argument being $n/3$, $3T(n/3)$ the front "3" that is multiplying the $T(n/3)$ is there to account for the three recursive calls. The function also does a triple nested loop.
So, the outer and iner loops each run $n^2$ times and then the middle loop runs $n$ times.
that gives you $n^2 * n * n^2 = n^5$. Together you get the relation $T(n)=3T(n/3) + n^5$. This is my recurrance realtion. Because the nested loops dominate the time complexity the tight bound for Big $O$ is $\theta (n^5)$

I used the recurrsion tree method to solve the reccurance relation:
```

The function makes 3 recursive calls to itself with the argument being n/3

0: Level 0 = n^5 // This is the total work on each level
1: Level 1 = 3*(n/3)^5 // Each level is multiplied by 3 becsaue of the three recursive calls
2: Level 2 = 9*(n/9)^5 // Multiplied by 3 again
3: Level 3 = 27*(n/27)^5 //and again.

This gives us a tree height of log_3(n) because of the dividing of n by 3 at each level.
so the total cost of work for each level = n^5 * log_3(n).
Then using the change of base formula (log_b(a) = log_c(a) / log_c(b)) you get n^5 * (log(n) / log(3)) .
log(3) is a constant so is ignored. n^5 grows faster then log(n) so the tight BIG O bound is equal to O(n^5)


```



Add your answer to this markdown file. [This
page](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions)
might help with the notation for mathematical expressions.

