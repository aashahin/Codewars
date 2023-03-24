# DESCRIPTION:
Implement a function sum that accepts arrays of integers and an optional callback and returns sum of results of callback function on each 'column' of arrays. In case callback is not specified, just return the sum.

Trivial example:
```
sum([1,2,3]) => 6
 1 + 2 + 3 = 6
 ```
Example #1:
```
sum([1,2,3], [4,5,6]) => 21
 1   2   3
 +   +   +
 4   5   6
 ↓   ↓   ↓
 5 + 7 + 9 = 21
 ```
Example #2:
```
sum([1,2,3], [4,5,6], (a, b) => a * b)) => 32
 1    2    3
 *    *    *
 4    5    6
 ↓    ↓    ↓
 4 + 10 + 18 = 32
 ```
Example #3:
```
sum([1,2,3], [4,5,6], [7,8,9], (a, b, c) => a * Math.pow(b, c)) => 31030722
     1        2          3
     *        *          *
     (        (          (
     4        5          6
     ^        ^          ^
     7        8          9
     )        )          )
     ↓        ↓          ↓
 16384 + 781250 + 30233088 = 31030722
 ```
In case arrays' lengths differ, replace non-existent values with zeroes, thus:
```
sum([1], [10, 20, 30]) => 61
  1    0    0
  +    +    +
 10   20   30
  ↓    ↓    ↓
 11 + 20 + 30 = 61
 ```
See example tests for more.

Input will always be VALID, i.e. at least one array (probably empty) will be passed to the function.

Good luck and have fun!

## Solution
```js
function sum(...args) {
    return typeof args[args.length-1] === 'function' ? [...Array(Math.max(...args.map(v=>v.length)))]
    .map((val,idx) => [...Array(args[args.length-1].length)].map((v,i) => args[i][idx]||0))
    .reduce((acc,val) => acc + args[args.length-1].apply(null,val),0) : args.reduce((acc,val)=> acc + val.reduce((a,b) => a+b,0),0)
  }
```