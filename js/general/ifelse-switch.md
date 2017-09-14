## Whats more performant, if..else or switch statements?

When considering this, the real question revolves around the speed which each one is able to handle a range of conditional statements.
<br>
<br>

### if statement
This is a typical example of a bad way of writting an if statement.
```js
if (value == 0){
    return result0;
} else if (value == 1){
    return result1;
} else if (value == 2){
    return result2;
} else if (value == 3){
    return result3;
} else if (value == 4){
    return result4;
} else if (value == 5){
    return result5;
} else if (value == 6){
    return result6;
} else if (value == 7){
    return result7;
} else if (value == 8){
    return result8;
} else if (value == 9){
    return result9;
} else {
    return result10;
}
```
<br>
This is beacause if the value happens to equal 9, it will have to check all the other statements before getting to the correct value.<br>
So the deeper the statement gets, more conditions have to be evaluated.<br>

There are ways however, to increase the performance of this, by writting your statement perhaps with a binary search algorithm. <br>
The aim of writting it this way is to try and evaluate as little conditions, for as many of the conditions as possible.
<br>
**Here's an example:**
```js
if (value < 6){

  if (value < 3){
    if (value == 0){
        return result0;
    } else if (value == 1){
        return result1;
    } else {
        return result2;
    }
  } else {
    if (value == 3){
        return result3;
    } else if (value == 4){
        return result4;
    } else {
        return result5;
    }
  }
} else {

  if (value < 8){
    if (value == 6){
        return result6;
    } else {
        return result7;
    }
  } else {
    if (value == 8){
        return result8;
    } else if (value == 9){
        return result9;
    } else {
        return result10;
    }
  }
}
```
<br>
This technically is written over more lines, however when evaluating these conditions it is able to skip over goups at a time, speeding it up.
<br>
However, the problem remains that each additional condition ends up taking more time to execute, affecting not only the performance but also the maintainability of this code.<br>
This is where the **switch statement** comes in.

### switch statement
A switch case is not only handy because it simplifies the performance of some conditions but also because it simplifies the appearance of the code.<br>
This is an exmaple of our first if statement we wrote but instead, using a switch statement.<br>
```js
switch(value){
    case 0:
        return result0;
    case 1:
        return result1;
    case 2:
        return result2;
    case 3:
        return result3;
    case 4:
        return result4;
    case 5:
        return result5;
    case 6:
        return result6;
    case 7:
        return result7;
    case 8:
        return result8;
    case 9:
        return result9;
    default:
        return result10;
}
```

<br>
In other programming languages the switch statement is always said to be the better option and this is because of how compilers are able to optimize them not the actual switch itself.<br>
But however because in javascript, different browsers, run different engines the switch statement varies in performance.<br>
For exmaple Firefox handles them really well, but Chrome, Safari, Opera and IE all show increases in the execution time as you get deeper into the switch statement.<br>
*However* those increases are smaller than the increases you would see with each additional condition of an if statement.<br>

## But which is better? 
In JavaScript, if statements are generally faster than switch statements ***WHEN*** there are just one or two conditions to be evaluated.<br>
When there are more than two conditions, ***AND*** the conditions are simple ***(not ranges)***, the switch statement seems to be faster.<br><br>
This is because the amount of time it takes to execute a single condition in a switch statement is often less than it takes to execute a single condition in an if statement, making the switch statement better only when there are a larger number of conditions.

## Array look ups
This is another alternative to the `if` and `switch` statements.<br>
```js
var results = [result0, result1, result2, result3, result4, result5, result6, result7, result8, result9, result10];

//return the correct result
return results[value];
```

<br>
This way works by storing all the values in an array which is the value is mapped to the index.<br>
So to retrieve the correct result you simply supply the value to the array to look up.<br>
This should only be used for large sets of data, as for small sets it is slower to look up an array than it is to evaluate an `if` statement.

## Best times to use each:
#### If statements:
- There are no more than two simple values to test.
- There are a large number of values that can be easily separated into ranges.

#### Switch statements:
- There are more than two but fewer than 10 simple values to test.
- There are no ranges for conditions because the values are nonlinear.

#### Array look up.
- There are more than 10 values to test.
- The results of the conditions are single values rather than a number of actions to be executed.