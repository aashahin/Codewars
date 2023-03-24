# Description
Build Tower
Build a pyramid-shaped tower, as an array/list of strings, given a positive integer number of floors. A tower block is represented with "*" character.

* For example, a tower with 3 floors looks like this:
```
[
  "  *  ",
  " *** ", 
  "*****"
]
And a tower with 6 floors looks like this:

[
  "     *     ", 
  "    ***    ", 
  "   *****   ", 
  "  *******  ", 
  " ********* ", 
  "***********"
]
```

## Solution
```javascript
function towerBuilder(nFloors) {
  // build here
  let arr = [];
    for (let i = 1; i <= nFloors; i++) {
        let str = "";
        for (let j = 1; j <= nFloors - i; j++) {
        str += " ";
        }
        for (let k = 1; k <= 2 * i - 1; k++) {
        str += "*";
        }
        for (let l = 1; l <= nFloors - i; l++) {
        str += " ";
        }
        arr.push(str);
    }
    return arr;
}
```
