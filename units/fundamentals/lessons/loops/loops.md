# Loops

## Objectives

## Vocabulary

* `while` loops
  * condition
* `for` loops
  * initialization
  * condition
  * increment

## Lesson

Consider a program that logs the numbers between 1 and 10:

```js
console.log(1)
console.log(2)
console.log(3)
...
```

This program isn't much fun to write, and it isn't very practical either. What if we wanted to log the numbers between 1 and 1000? There is a better solution than writing this by hand: **loops**. Loops are really a solution for many repetitive tasks.

## The `while` loop

Now you are hopefully convinced that loops can be a good idea. Our first loop is the **while** loop. It is similar to the **if** statement, in that we will check if some condition is true. Unlike the **if** statement, we will execute the code block following the while loop again and again, as long as the condition is true. Whenever we reach the bottom of the code block, we go right back up and check the condition again.

```js
var num = 1
while (num <= 10) {
  console.log('the number is: ' + num)
}
```

If you try to run the code above, the number `1` will be logged repeatedly. Eventually, your computer will freeze or you will see an error message. This is because we are repeatedly checking if the value of `num` is smaller than 10. If it is smaller, we log the value of `num`, and check again. Since the value of `num` never changes, we just keep logging `1`, until the computer runs out of memory. To fix this, we need to change the value of `num` inside the code block. In this instance, we will increase the value by `1` every time.

```js
var num = 1
while (num <= 10) {
  console.log('the number is: ' + num)
  num += 1
}
```

It works! Run the program and you will see that the numbers from 1 to 10 are logged to the screen. But what if we want to log only the odd numbers (3, 5, 7, 9). In that case, we just need to increase number by `2` every time.

```js
var num = 1
while (num < 10) {
  console.log('the number is: ' + num)
  num += 2
}
```

> Ex 1. Write a `while` loop that logs all the even numbers between 2 and 100.
> Ex 2. Write a `while` loop that logs all the odd numbers starting from 99, and going down to 1.

### The `for` loop

Another kind of loop, the `for` loop, is just a condensed version of the while loop. With the for loop we create a variable, check a condition, and change the variable's value, all in one line.

```js
for (var num = 1; num < 10; num += 1) {
  console.log(num)
}
```

The above loop logs the numbers between 1 and 10, just like the while loop above. Generally speaking, the structure of the `for` is the same every time. There are two semicolons. The part before the first semicolon defines a variable. The second part is a boolean expression that checks if the loop should continue. The last part updates the variable we created after every iteration. More formally, this is what each part is called:

```js
for ([initialization]; [condition]; [increment]){

}
```

### More complex problems

Loops can be used to solve pretty complex problems. Earlier, when we wanted to log only even or only odd values, we changed the increment from `1` to `2`. But what if we want to count both even and odd numbers, and do something different for each? Let's say we want to log for each number: `'even'` if it is even, and `'odd'` if it is odd. For this kind of problem we can use the remainder operator: `%`. We will make a loop that increments a variable by `1`, and inside the code block check if the variable is even or odd. To do this we check the remainder of division by `0`: if there is no remainder, the number is even. Otherwise the number is odd.

```js
for (var i = 0; i <= 10; i += 1){
  if (i % 2 === 0){
    console.log(i + ' is even')
  } else {
    console.log(i + ' is odd')
  }
}
```

When you run this program, you will see the following:

<pre>
0 is even
1 is odd
2 is even
...
9 is odd
10 is even
</pre>

We can also use a loop to calculate the sum of all the number between 1 and 10:

```js
var sum = 0
for (var i = 1; i <= 10; i += 1){
  sum += i
}
```

We can write a chart to see what's going on more closely:

|i   | sum   |
|:--:|:-----:|
| 1  | 1     |
| 2  | 3     |
| 3  | 6     |
| 4  | 10    |
| 5  | 15    |
| 6  | 21    |
| 7  | 28    |
| 8  | 36    |
| 9  | 45    |
| 10 | 55    |

You may have noticed that to find the value of `sum` in every new row, we take the existing value of sum and add it to the value of `i` in the next row. It is often useful to write things out in this fashion. It can help clear things up.

### Changing the increment

So far we've been incrementing a variable by `1` on each iteration of the loop. We can increment by other numbers as well.

```js
// logging all multiples of 5 between 5 and 50
for (var i = 5; i <= 50; i += 5) {
  console.log(i)
}
```

We can also decrement instead of incrementing:

```js
// logging all multiples of 5 between 50 and 5, descending
for (var i = 50; i >= 5; i -= 5){
  console.log(i)
}
```

> Ex. Log all multiples of 10 between 10 and 100
> Ex. Log all multiples of 10 between 100 and 0, descending

## Loop exercises

* Write a function that takes a number as an argument and logs all the numbers, descending, between the number and 1.
* Write a a function that takes a number `num` as an argument, and iterates over all numbers from 0 to `num`. For each iteration, it will check if the current number is even or odd, and log that to the screen (e.g. "2 is even")
* Write a function that takes a number `num` as an argument and iterates over all numbers from 0 to `num`. For each iteration of the loop, it will multiply the number by 9 and log the result (e.g. "2 * 9 = 18")
* Use the `assignGrade` function from unit 4 (functions). Create a loop that will iterate over the numbers from `60` to `100`. For each number, it will call `assignGrade` with that number as an argument.

### Bonus

* Write a function that uses console.log to log all the numbers from 1 to 100, with two exceptions. For numbers divisible by 3, log "Fizz" instead of the number, and for numbers divisible by 5 (and not 3), log "Buzz" instead.

When you have that working, modify your program to log "FizzBuzz", for numbers that are divisible by both 3 and 5 (and still log "Fizz" or "Buzz" for numbers divisible by only one of those).
