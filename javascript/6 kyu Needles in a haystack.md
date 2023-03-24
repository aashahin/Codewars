# DESCRIPTION:
Find the needle(s) in a haystack by creating a function that returns all properties (recursively) which contains the needle (string).

Return value should be a sorted array.

### Example:

```js
var obj = {
  site: "Codewars",
  description: "Lorem ipsum dolor sit...",
  obj2: {
    str: "Yeah, Codewars!",
    num: 123,
    obj3: {
      something: "Ph'nglui mglw'nafh Codewars R'lyeh wgah'nagl fhtagn. Gotha fm'latgh h'gof'nn, geb chtenff"
    }
  }
};
var results = search(obj, "Codewars"); //results = ["obj2.obj3.something", "obj2.str", "site"]
```
## Solution
```js
function search(haystack, needle) {
  let response = [];
  for (const [key, value] of Object.entries(haystack)) {
    if (typeof(value) === "string" && value.indexOf(needle) >= 0) {
      response.push(key);
    } else if (value !== null && value.constructor.name === "Object") {
      response = response.concat(search(value, needle).map(x=>key + "." + x));
    }
  }
  return response.sort();
}
```