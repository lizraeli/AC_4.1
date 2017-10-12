# Big O Notation

**Big O Notation** is a way of measuring how performance of an algorithm relative to how many items you give it as input.

We measure two types of performance with Big O Notation:

- **Time Complexity**: How long does it take an algorithm to run when given *n* elements as input?

- **Space Complexity**: How much memory does an algorithm need when given *n* elements as input?

We usally talk much more about time complexity.

## Common Time Complexities of Algorithms

|Big O Runtime|Name|Example|
|---|---|---|
|O(1) | Constant | Print the first string in an array of count *n* |
|O(n) | Linear | Print every string in an array of count *n* |
|O(n<sup>2</sup>) | Quadratic | Print every character of every string in an array of count *n* (Assume that every string is also of length n) |

### O(1)

```js
function constantTime(arr) {
    console.log(arr[0])
}
```

Let's assume it takes 10 ms to print a string.

|arr.length (n) | Runtime |
|---|---|
| 1 | 10 ms |
| 10 | 10 ms |
| 100 | 10 ms |

We can see that the time it takes to run `constantTime` does not vary.  No matter how large *n* is, it will always take a constant amount of time to run our function.

### O(n)

```js
function linearTime(arr) {
    arr.forEach(function(str) {
       console.log(str)
    })
}
```

|arr.length (n) | Runtime |
|---|---|
| 1 | 10 ms |
| 10 | 100 ms |
| 50 | 500 ms |
| 1000 | 10,000 ms = 10 s |

In this example, increasing the size of our array does increase how long it takes our function to run.  Going back to our days with algebra, we can even make a math function that explaines the relationship between the count and the runtime:

<details>
  <summary>What is the relationship? </summary>
   f(n) = 10n
</details>

<details> 
  <summary>What is the time complexity? </summary>
   O(n)
</details>

#### Where'd the 10 go (?)

- Big O notation only cares about the big picture.  While it can be very relevant for our code to make something 10 times faster, Big O is only used to tell you the rough area you're in.
- One main reason for this is that the 10 ms figure isn't a part of our algorithm.  If we used a better computer, it might only take 1 ms to print a string.  Big O doesn't know what computer you're using, so it generalizes to *linear time*.

### O(n<sup>2</sup>)

```js
//Print out who selected which character.  Two players can select the same character.
function quadraticTime(characterNames) {
    for (var i = 0; i < characterNames.length; i++) {
        for (var j = 0; j < characterNames.length; j++ ) {
                console.log("Player One: " + characterNames[i] + " Player Two: " + characterNames[j]))
        }
    }
}
```

This one's a little more complicated.  Let's break it down.

Our code will then print out each pair of names.  Here's are a few sample inputs and outputs:


**Input: ["Agnes"]**

<details> 
  <summary> Output: </summary>
    Player One: Agnes, Player Two: Agnes
</details>

**Input: ["Agnes", "Bart"]**
<details> 
  <summary> Output: </summary>

    Player One: Agnes, Player Two: Agnes
    Player One: Agnes, Player Two: Bart
    Player One: Bart, Player Two: Agnes
    Player One: Bart, Player Two: Bart
    
</details>

**Input: ["Agnes", "Bart", "Carl"]**
<details> 
  <summary> Output: </summary>
    
    Player One: Agnes, Player Two: Agnes
    Player One: Agnes, Player Two: Bart
    Player One: Agnes, Player Two: Carl
    Player One: Bart, Player Two: Agnes
    Player One: Bart, Player Two: Bart
    Player One: Bart, Player Two: Carl
    Player One: Carl, Player Two: Agnes
    Player One: Carl, Player Two: Bart
    Player One: Carl, Player Two: Carl
    
</details>

**Input: ["Agnes", "Bart", "Carl", "Duffman"]**
<details> 
  <summary> Output: </summary>
    
    Player One: Agnes, Player Two: Agnes
    Player One: Agnes, Player Two: Bart
    Player One: Agnes, Player Two: Carl
    Player One: Agnes, Player Two: Duffman
    Player One: Bart, Player Two: Agnes
    Player One: Bart, Player Two: Bart
    Player One: Bart, Player Two: Carl
    Player One: Bart, Player Two: Duffman
    Player One: Carl, Player Two: Agnes
    Player One: Carl, Player Two: Bart
    Player One: Carl, Player Two: Carl
    Player One: Carl, Player Two: Duffman
    Player One: Duffman, Player Two: Agnes
    Player One: Duffman, Player Two: Bart
    Player One: Duffman, Player Two: Carl
    Player One: Duffman, Player Two: Duffman
    
</details>


Let's format the count of the array, number of print statements and the runtime.


|arr.length (n) | Number of print statements | Runtime |
|---|---|---|
| 1 | 1 | 10 ms |
| 2 | 4 | 40 ms |
| 3 | 9 | 90 ms |
| 4 | 16 | 160 ms |

<details>
    <summary> What function describes the relationship between *n* and the runtime? </summary>
    f(n) = 10n<sup>2</sup>
</details>
    
<details>
    <summary> What is the time complexity? </summary>
    O(n<sup>2</sup>)
</details>


We can then extrapolate to fill in the same chart we were using above.

|arr.length (n) | Runtime |
|---|---|
| 1 | 10 ms |
| 10 | 1000 ms = 1 s |
| 50 | 25000 ms = 25 s |
| 1000 | 10,000,000 ms = 2.78 hours |

That gets slow fast!

Let's put all the charts together:

|arr.length (n) | Runtime: O(1) | Runtime: O(n) | Runtime: O(n<sup>2</sup>) |
|---|---|---|---|
| 1 | 10 ms | 10 ms |10 ms |
| 10 | 10 ms | 100 ms | 1000 ms = 1 s |
| 50 | 10 ms | 500 ms | 25000 ms = 25 s |
| 1000 | 10 ms | 10,000 ms = 10 s | 10,000,000 ms = 2.78 hours |

## Other Runtimes

**Note**: log(n) means log<sub>2</sub>(n)

We'll get to these all going forwards.  Don't worry about them too much right now.

|Big O Runtime|Name|Example|
|---|---|---|
|O( log(n) )| Logarithmic | Binary Search |
|O(n * log(n)) | Linearithmic | Merge Sort/Quick Sort |
|O(2<sup>n</sup>) | Exponential | Recursive Fibonacci |
|O(n!) | Factorial | Generate all the permutations of a list |

## Ranking and Visualizing Big O Runtimes

From fastest to slowest:

O(1) < O(log(n)) < O(n) < O(nlog(n)) < O(n<sup>2</sup>) < O(2<sup>n</sup>) < O(n!)

The following graph is from [http://bigocheatsheet.com](http://bigocheatsheet.com) 
![From Big O Cheat Sheet](assets/big_o_chart.png)

## Deriving Runtime

We just saw an example of how to derive the runtime of a function.  Let's try it with some similar examples.

```js
function exampleOne(arr, target) {
    for (var i = 0; i < arr.length; i++) {
        if (arr[i] === target){
            return true
        }
    }
    return false
}
```

<details>
    <summary>what is the time complexity of `exampleOne`?</summary>
    O(n)
</details>

<details>
    <summary> Explanation: </summary>
    We might need to look at each of the n elements inside `arr`.  "n" here represents arr.length  The more elements we have in our array, the longer it will take to find our target element.
</details>
<br/>

```js
func exampleTwo(arr) {
    for (var i = 0; i < 1000000; i++) {
        console.log("Many printings!");
    }
}
```

<details>
    <summary>what is the time complexity of exampleTwo(arr:)?</summary>
    O(1)
</details>

<details>
    <summary>Explanation: </summary>
    No matter how big our array is, this will always print "Many printings" 1,000,000 times.  While this would take a really long time, it is always the ***same*** amount of time.  It will take a constant time to run this function and it is entirely independant of the count of arr.
</details>
<br/>

```js
function exampleThree(arr) {
   var counter = 0
   arr.forEach(function(num) {
       if (arr.indexOf(num + 1) !== -1) {
           counter += 1
       }
   })
   return counter
}
```

<details>
    <summary>what is the time complexity of `exampleThree`?</summary>
    O(n<sup>2</sup>)
</details>

<details>
    <summary>Explanation: </summary>
    Our for loop goes over each of *n* Ints.  Then for each of those Ints, we run contains, which will go over each of *n* Ints.  We would then end up looking at *n<sup>2</sup>* Ints in total.
</details>
<br/>

## Worst Case, Average Case and Best Case

Usually when we talk about runtime, we talk about the *Average Case* runtime.  This is what we would expect the algorithm to do with a typical data set.  Sometimes is also makes sense to talk about the *Best Case* or *Worst Case* situation.  In these cases, we can make special assumptions about the input and see what the minimum possible or maximum possible runtimes are.

Example:

```js
function bestAverageAndWorstFunc(arr) {
    if (arr.length < 3 || arr[0] == 8675309) {
        return undefined;
    } else if (arr[0] + arr[1] === 24601) {
        arr.forEach(function(elem1) {
            arr.forEach(function(elem2) {
                console.log("Gotcha!")
            }
        }
    } else {
        arr.forEach(elem) {
            console.log(elem)
        }
    }
}
```

<details>
    <summary>Best Case Runtime</summary>
    O(1)
</details>

<details>
    <summary>Worst Case Runtime</summary>
    O(n<sup>2</sup>)
</details>

<details>
    <summary>Average Case Runtime</summary>
    O(n)
</details>

In most situations, the average case runtime and the worst case runtime are the same.  But it's good to know the difference.

Examples (copied from the previous section) 

```js
function exampleOne(arr, target) {
    for (var i = 0; i < arr.length; i++) {
        if (arr[i] === target){
            return true;
        }
    }
    return false
}
```

<details>
    <summary> What is the *worst case* runtime for `exampleOne`? </summary>
    O(n)
</details>

<details>
    <summary> What is the *best case* runtime for exampleOne(array:withCharacter:)? </summary>
    O(1)
</details>


<details>
    <summary>Explanation:</summary>
    In the worst case situation, our target character is always at the end of the array.  We would need to look at each of *n* elements before we would find it.  
    In the best case situation, our target character is always first, so we only ever need to look at 
    one thing.
</details>

```js
func exampleTwo(arr) {
    for (var i = 0; i < 1000000; i++) {
        console.log("Many printings!");
    }
}
```

<details>
    <summary> What is the *worst case* runtime for exampleTwo(arr:)? </summary>
    O(1)
</details>


<details>
    <summary> What is the *best case* runtime for exampleTwo(arr:)? </summary>
    O(1)
</details>

<details>
    <summary>Explanation:</summary>
    This will do the same thing no matter what the input is.
</details>

```js
func exampleThree(arr) -> Int {
   var counter = 0
   for num in arr {
       if arr.contains(num+1) {
           counter += 1
       }
   }
   return counter
}
```

<details>
    <summary> What is the *worst case* runtime for `exampleThree`? </summary>
    O(n<sup>2</sup>)
</details>


<details>
    <summary> What is the *best case* runtime for `exampleThree`? </summary>
    O(n)
</details>

<details>
    <summary>Explanation:</summary>
    In the worst case situation, our array looks something like [1,4,7,10,13,16].  Contains will always search the full length of the array for each element.  This menas that we would look at *n* elements *n* times. In the best case, our array looks something like [3,2,2,2,2,2,2].  We still need to look at every element once, but contains could stop on the first Int each time.
</details>


## Compound Runtimes

So far, we've been working with functions with either a nested loop, or a single loop.  What happens when we have multiple different runtimes in sequence?  Let's look at an example:

```js
function compoundRuntimes(arr) {
    for (var i = 0; i < 1000; i++) {
        console.log("Hi!")
    }
    arr.forEach(function(elem) {
        console.log(elem)
    })

    arr.forEach((elem1, index1){
        arr.forEach((elem2, index2){
            if (index1 !== index2 && elem1 === elem2){
                console.log("found two identical elements")
            }
        })
    })
}
```

<details>
    <summary>How long would it take to run this code?</summary>
    O(1) + O(n) + O(n<sup>2</sup>)
</details>

Let's see how the runtime increases with count using our chart from above

|arr.length (n) | Runtime: O(1) | Runtime: O(n) | Runtime: O(n<sup>2</sup>) | <details><summary>compoundRuntimes(arr:)</summary>Runtime: O(1) + O(n) + O(n<sup>2</sup>) |
|---|---|---|---|---|
| 1 | 10 ms | 10 ms |10 ms | 30 ms |
| 10 | 10 ms | 100 ms | 1000 ms = 1 s | 1110 ms = 1.11 s |
| 50 | 10 ms | 500 ms | 25000 ms = 25 s | 25510 ms = 25.51 s |
| 1000 | 10 ms | 10,000 ms = 10 s | 10,000,000 ms = 2.78 hours | 10,010,010 ms = 2.78 hours |

As the count gets bigger and bigger, the only term that matters is the O(n<sup>2</sup>) term.  Therefore, we say that the runtime of compoundRuntimes(arr:) is O(n<sup>2</sup>)

When we have a compound runtime, we only keep the ***most significent*** term.  In fact, the O in *Big O Notation* stands for "Order" because we care most about the "Biggest Order" that appears.  Order in this case is talking about the [order of the algebraic function](https://en.wikipedia.org/wiki/Order_of_a_polynomial) also called the [degree](https://en.wikipedia.org/wiki/Degree_of_a_polynomial).

## Compound Runtime Examples

For the examples below, give the average case runtime

### Example One

```js
function doStuff(arr) {
    arr.forEach(function(elem1) {
        arr.forEach(function(elem2) {
            arr.forEach(function(elem3) {
                console.log(elem3)
            })
        })
    })
}
```

<details>
    <summary>what is the time complexity of doStuff?</summary>
    O(n<sup>3</sup>)
</details>

### Example Two

```js
function doOtherStuff(arr) {
    arr.forEach(function(elem) {
        console.log(num)
    })

    arr.forEach(function(elem) {
        arr.forEach(function(elem) {
            console.log(elem)
        })
    })

    arr.forEach(function(elem) {
        console.log(elem)
    })
}
```

<details>
    <summary>what is the time complexity of doOtherStuff?</summary>
    O(n<sup>2</sup>)
</details>

### Example Three

```js
function foo(myArr) {
    myArr.forEach(function(elem) {
        console.log(elem)
    })
}

function bar(myArr) {
    myArr.forEach((elem)  {
        foo(myArr)
    })
}
```

<details>
    <summary>what is the time complexity of foo?</summary>
    O(n)
</details>

<details>
    <summary> what is the time complexity of bar? </summary>
    O(n<sup>2</sup>)
</details>

### Example Four

```js
function secondSmallest(myArr) {
    var min = myArr[0];
    var minIndex = 0;
    myArr.forEach(function(num, index) {
        if (num < min) {
            min = num;
            minIndex = index;
        }
    })

    var secondMin = min === myArr[0] ? myArr[1] : myArr[0]

    myArr.forEach(function(num, index) {
        if (num < secondMin && index !== minIndex) {
            secondMin = num;
        }
    })

    return secondMin
}
```

<details>
    <summary> what is the time complexity of secondSmallest </summary>
    O(n)

    We have O(n) + O(n), but as n gets bigger and bigger, we only care about the highest order.

</details>

### Questions

1. So far looking for an element in an array has taken us `O(n)` time. If you know that the array is sorted, is there a way to have a faster lookup? What would be its time complexity? An example of a sorted array:

```js
var arr = [2, 4, 5, 10, 22, 120, 2480]
```