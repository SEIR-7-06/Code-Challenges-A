# findOdd

<!-- [REPL](https://repl.it/@michaelpetty/findOdd#index.js) -->

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
function findOddOccurrence(arrayOfNums) {
  let oddOccuringNum = null;

  // Loop through the array
  for (let i = 0; i < arrayOfNums.length; i++) {
    // for each interger

    // find the number of occurences of that integer
    let occurences = 0;

    for (let j = 0; j < arrayOfNums.length; j++) {
      if (arrayOfNums[j] === arrayOfNums[i]) {
        occurences += 1;
      }
    }

    // if occurrences is odd set oddOccuringNum to integer
    if (occurences % 2 === 1) {
      oddOccuringNum = arrayOfNums[i];
    }
  }

  return oddOccuringNum;
}


///////////////////////////////////////////////////////
// SOLUTION 2 - Using forEach
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


///////////////////////////////////////////////////////
// SOLUTION 3
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

# Convert to CamelCase

<!-- [REPL](https://repl.it/@michaelpetty/camelCase#index.js) -->

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

<hr>

# Regex PIN Validator

<!-- [REPL](https://repl.it/@michaelpetty/RegexPINValidator#index.js) -->

ATM machines allow 4 or 6 digit PIN codes and PIN codes cannot contain anything but exactly 4 digits or exactly 6 digits.

If the function is passed a valid PIN string, return true, else return false.

eg:
```javascript
validatePIN("1234") === true
validatePIN("12345") === false
validatePIN("a234") === false
```

<hr>

## Solution
<details>
<summary>Click here to reveal a possible solution.</summary>
<p>
  
  ```javascript
  // a solution, but nothing special 
  function validatePIN(pin) {
    //return true or false
    var n = pin.length;
    if( n != 4 && n != 6)
        return false;
    for (var i in pin)
        if (pin[i] > '9' || pin[i] < '0')
            return false;
    return true;
  }
  
  // good solution
  function validatePIN(pin) {

    var pinlen = pin.length;
    var isCorrectLength = (pinlen == 4 || pinlen == 6);
    var hasOnlyNumbers = pin.match(/^\d+$/);

    if(isCorrectLength && hasOnlyNumbers){
      return true;
    }

    return false;

  }
  
  // cleanest solution
  function validatePIN(pin) {
    return /^(\d{4}|\d{6})$/.test(pin)
  }
  ```
</p>
</details>

<hr>
