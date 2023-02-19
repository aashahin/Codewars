# DESCRIPTION:
Write a function which calculates the average of the numbers in a given list.

``Note: Empty arrays should return 0.``



## The Solution:

```
function findAverage(array) {
  return array.length ? array.reduce((acc,curr)=> acc+curr) / array.length:0;
}
```