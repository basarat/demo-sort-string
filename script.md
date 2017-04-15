# Case insensitive sorting for string arrays
> We look at the default `Array.prototype.sort` behavior and discuss how you can to case insensitive sorts

Here we have an array of a few strings.

```js
const foo = [
  'Alpha',
  'beta',
  'Gamma',
  'delta'
];
foo.sort();
foo.forEach(x=>console.log(x));
```

* If we go ahead and sort them you can see that `Gamma` appears before beta.
* This is because the default string sorting is case sensitive and capital case strings come before lower case strings in their unicode code points.

```js
// A a
```

* To do case insensitive sorting you can provide a custom comparer function to Array prototype sort.
* You take two strings
* then you use the string prototype localeCompare function for the first string compare it to the  second.

```js
foo.sort((a, b) => a.localeCompare(b));
```

* Now there are a few ways of adding case insensitivity to this but the simplest one with the greatest browser support is to simply convert both strings to lower case before doing the comparison.

```js
const foo = [
  'Alpha',
  'beta',
  'Gamma',
  'delta'
];
foo.sort((a, b) => a.toLowerCase().localeCompare(b.toLowerCase()));
foo.forEach(x => console.log(x));
```
