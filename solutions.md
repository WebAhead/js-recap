# JS recap solution

This is the solution for the JavaScript recap workshop, **only look at it in case you have solved the question** and want to check different solutions.

1. Format a string

  Your task was to loop over the object keys and return the value concatenated

  Mario's solution

  ```js
  function list(names) {
    var sentance = "";
    names.forEach(({ name: item }, index) => {
      var namesLength = names.length;

      if (index + 1 === namesLength && namesLength !== 1) {
        sentance += " & ";
      } else if (index !== 0) {
        sentance += ", ";
      }
      sentance += item;
    });

    return sentance;
  }
  ```

  Fancy regex solution, joins the string with `,` and replaces either the one or last one with `&`

  ```js
  function list(names) {
    return names
      .map(e => e.name)
      .join(", ")
      .replace(/,(?=[^,]*$)/, " &");
  }
  ```

2. Count the divisible numbers

  This is your typical for loop case, you need to loop over the numbers and check which are divisible by k

  ```js
  function divisibleCount(x, y, k) {
    var count = 0;
    for (var i = x; i <= y; i++) {
      if (i % k === 0) {
        count++;
      }
    }
    return count;
  }
  ```

  The more mathematical solutions

  ```js
  function divisibleCount(x, y, k) {
    return Math.floor(y / k) - Math.floor((x - 1) / k);
  }
  ```

3. Sorting arrays alphabetically

  The following solution is sorting the array by always comparing the first letter of each 2 words lower-cased

  ```js
  // input: names - unsorted strings
  // output: case-agnostic sort
  sortme = function(names) {
    return names.sort(function(a, b) {
      var letter1 = a.toLowerCase().charAt(0);
      var letter2 = b.toLowerCase().charAt(0);
      return CompareForSort(letter1, letter2);
    });
  };

  function CompareForSort(first, second) {
    if (first == second) return 0;
    if (first < second) return -1;
    else return 1;
  }
  ```

4. Unique in order

  Another typical case for using a for loop

  ```js
  var uniqueInOrder = function(iterable) {
    var result = [];
    for (var i = 0; i < iterable.length; i++) {
      if (iterable[i - 1] === undefined || iterable[i - 1] !== iterable[i]) {
        result.push(iterable[i]);
      }
    }
    return result;
  };
  ```

5. Longest palindrome

  This question can be solved by counting the letters you encounter, you need to check that you have an even number of letters for each letter and one that is odd

  ```js
  function longestPalindrome(str) {
    var s = str.toLowerCase();
    var arr = "abcdefghijklmnopqrstuvwxyz0123456789";
    var count = 0;
    for (var i = 0; i < arr.length; ++i) {
      var c = 0;
      for (var j = 0; j < s.length; ++j) if (s[j] == arr[i]) c++;
      count += Math.floor(c / 2) * 2;
    }
    return count == s.length ? count : ++count;
  }
  ```
