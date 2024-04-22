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
        // This contributes to the 3T(n/3) part of the recurrence relation
        mystery(n / 3);

        // Initialize count variable
        var count = 0;

        // Another recursive call to mystery function with n divided by 3
        // This also contributes to the 3T(n/3) part of the recurrence relation
        mystery(n / 3);

        // Nested loop structure
        // The outer loop runs n^2 times
        for (var i = 0; i < n * n; i++) {
            // The middle loop runs n times
            for (var j = 0; j < n; j++) {
                // The inner loop runs n^2 times
                // The total time complexity of these nested loops is O(n^5), which contributes to the n^5 part of the recurrence relation
                for (var k = 0; k < n * n; k++) {
                    
                    count = count + 1;
                }
            }
        }

        // Another recursive call to mystery function with n divided by 3
        // This also contributes to the 3T(n/3) part of the recurrence relation
        mystery(n / 3);
    }
}
```

The function makes 3 recursive calls to itself, and then has a triple nested loop that runs $n^5$ times. The time complexity tree is
```javascrirpt
Tree Levels:
Level 0:                     n^5
Level 1:          3*(n/3)^5
Level 2:     9*(n/9)^5
Level 3: 27*(n/27)^5
```
So, the height of the tree is $log_3(n)$ because each level $n$ is being divided by 3. Each level cost $n^5$. The time complexity is $(n^5)*log_3(n)$ or $O(n^5 * log(n))$




Add your answer to this markdown file. [This
page](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions)
might help with the notation for mathematical expressions.

