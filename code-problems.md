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
// SOLUTION 1
function findOddOccurrence(array) {
  let oddOccuringNum = null;

  // Loop through array
  array.forEach((int) => {
    // for each int
      
    // find number of occurrences
      let occurrences = 0;

      array.forEach((num) => {
        if (num === int) {
          occurrences += 1;
        }
      });

      // if occurrences is odd return
      if (occurrences % 2 === 1) {
        oddOccuringNum = int;
      }
  });

  return oddOccuringNum;
}

// SOLUTION 2
// Loop through array
  // for each int
  // find number of occurrences
  // if occurrences is odd return int
function findOddOccurrence(array) {
  return array.find((int) => {
    const occurrences = array.filter(num => num === int).length;
    return occurrences % 2 === 1;
  });
}
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
function findSmallestInt(args) {
  // Happy coding!  
}
```

<hr>

## Solution

<details>
  <summary>Click here to reveal a possible solution.</summary>
  <p>

```javascript
// SOLUTION 1
function findSmallestInt(array) {
  let smallestInt = null;

  // Loop through array
  array.forEach((int) => {
    if (smallestInt === null) {
      smallestInt = int;
    } else {
      // if number is smallest so far make it new smallest number
      if (int < smallestInt) {
        smallestInt = int;
      }
    }
  });
  // return the smallest number
  return smallestInt;
}

///////////////////////////////////////////////////////
// SOLUTION 2
function findSmallestInt(array) {
  return array.reduce((smallest, int) => {
    return int < smallest ? int : smallest;
  }, Infinity);
}

///////////////////////////////////////////////////////
// SOLUTION 3
function findSmallestInt(array) {
  return Math.min(...array);
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
// SOLUTION 1
function toCamelCase(phrase) {
  // If phrase contains - split on -
  let splitChar = '';
  if (phrase.includes('-')) {
    splitChar = '-';
    // If phrase contains _ split on _
  } else if (phrase.includes('_')) {
    splitChar = '_';
  }

  const words = phrase.split(splitChar);

  // Loop through each word
  const wordsWCaps = words.map((word, index) => {
    // Capitalize first letter of each word
    if (index === 0) {
      return word;
    }
    return word.charAt(0).toUpperCase() + word.slice(1);
  });

  // Join words and return
  return wordsWCaps.join('');
}


// convert string to array of words
// Loop through array
  // for each word after 1st, convert to capital casing
  // join words into single string

// SOLUTION 2
function toCamelCase(phrase) {
  const words = phrase.split(/[-_]/);

  const convertedWords = words.map((word, index) => {
    if (!index) return word;
    return word.charAt(0).toUpperCase() + word.slice(1);
  });

  return convertedWords.join('');
}

  ```
  </p>
</details>
