# findOdd

[REPL](https://repl.it/@michaelpetty/findOdd#index.js)

Given an array, find the int that appears an odd number of times. Assume there will always be only one integer that appears an odd number of times.

```javascript
function findOdd(array) {
  // happy coding!
}

// Tests:
findOdd([20,1,-1,2,-2,3,3,5,5,1,2,4,20,4,-1,-2,5]);
// => 5

findOdd([1,1,2,-2,5,2,4,4,-1,-2,5]);
// => -1

findOdd([20,1,1,2,2,3,3,5,5,4,20,4,5]);
// => 5

findOdd([10]);
// => 10

findOdd([1,1,1,1,1,1,10,1,1,1,1]);
// => 10

findOdd([5,4,3,2,1,5,4,3,2,10,10]);
// => 1
```

<hr>

## Solution

<details>
  <summary>Click here to reveal a possible solution.</summary>
  <p>

  ```javascript
  // decent solution, bad efficiency
  function findOdd(array) {
    // object to serve as counter for all the items in the array (the items will be the keys, the counts will be the values)
    var obj = {};
    array.forEach(function(e) {    // for each item e in the array
      if(obj[e]) {
        obj[e]++;       // if we already encountered this item, then increments the counter
      } else {
        obj[e] = 1;     // otherwise start a new counter (initialized with 1)
      }
    });

    // select only the numbers that occured an odd number of times
    var result;                   // the result
    for(var e in obj) {           // for each key e in the hash (the key are the items of the array)
      if(obj[e] % 2) {            // if the count of that item is an odd number, set its value to result and break loop
        result = parseInt(e);
      }
    }


    return result;
  }
  
  // better solution
  function findOdd(A) {
    var obj = {};
    A.forEach(function(el){
      obj[el] ? obj[el]++ : obj[el] = 1;
    });

    for(prop in obj) {
      if(obj[prop] % 2 !== 0) return Number(prop);
    }
  }
  
  // best solution (even better if you explain why it works)
  const findOdd = (xs) => xs.reduce((a, b) => a ^ b);
  ```

</p>
</details>

<hr>

# SmallestInt

[REPL](https://repl.it/@michaelpetty/smallestInt)

Given an array of integers your solution should find the smallest integer.

For example:
```
Given [34, 15, 88, 2] your solution will return 2
Given [34, -345, -1, 100] your solution will return -345
```

You can assume, for the purpose of this problem, that the supplied array will not be empty.

```javascript
class SmallestIntegerFinder {
  findSmallestInt(args) {
    // Happy coding!  
  }
}
```

<hr>

## Solution

<details>
  <summary>Click here to reveal a possible solution.</summary>
  <p>

  ```javascriptclass 
  // basic solution
  SmallestIntegerFinder {
    findSmallestInt(args) {
      var lowest;
      for(var i in args){
        if(i==0){
          lowest = args[i];
        }
        else {
          if(lowest >= args[i]){
          lowest = args[i];
          }
        }
      }
      return lowest;
    }
  }
  
  // better
  class SmallestIntegerFinder {
    findSmallestInt(args) {
      return args.sort((a,b)=>a-b)[0];
    }
  }
  
  // best
  class SmallestIntegerFinder {
    findSmallestInt(args) {
      return Math.min(...args)
    }
  }
  ```

</p>
</details>

<hr>

# Convert to CamelCase

[REPL](https://repl.it/@michaelpetty/camelCase#index.js)

Complete the method/function so that it converts dash/underscore delimited words into camel casing. The first word within the output should be capitalized only if the original word was capitalized (known as Upper Camel Case, also often referred to as Pascal case).

Examples:
```javascript
toCamelCase("the-stealth-warrior") // returns "theStealthWarrior"

toCamelCase("The_Stealth_Warrior") // returns "TheStealthWarrior"
```

<hr>

## Solution

<details>
  <summary>Click here to reveal a possible solution.</summary>
  <p>

  ```javascript
  // inelegant solution (still a solution!)
  function toCamelCase(str){
    var strArray;

    if (str.indexOf('-') !== -1){ //if delineated by -
      strArray = str.split('-');
    } else {
      strArray = str.split('_');  //if delineated by _
    }

    var camelCase = strArray[0]; //keeps first word value as is

    for (var i=1, len=strArray.length; i < len; i++){
      var capitalized = strArray[i].substr(0, 1).toUpperCase() + strArray[i].slice(1);
      camelCase += capitalized;
    }

    return camelCase;
  }

  // longform solution (3 functions)
  function toCamelCase(str){
    return str.split(/\-|_/).reduce(function(previous, current, index){ return camelize(previous, current, index);});
  }

  function camelize(previous, current, index){
    return previous + current.capitalizeFirstLetter();
  }

  String.prototype.capitalizeFirstLetter = function() {
      return this.charAt(0).toUpperCase() + this.slice(1);
  }

  // best solution
  function toCamelCase(str){
    var regExp=/[-_]\w/ig;
    return str.replace(regExp,function(match){
          return match.charAt(1).toUpperCase();
     });
  }
  ```
  </p>
</details>
