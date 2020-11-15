# [How to uppercase the first letter of a string in JavaScript][Website]

JavaScript offers many ways to capitalize a string to make the first character uppercase. Learn the various ways, and also find out which one you should use, using plain JavaScript


One of the most common operations with strings is to make the string capitalized: uppercase its first letter, and leave the rest of the string as-is.


The best way to do this is through a combination of two functions. One uppercases the first letter, and the second slices the string and returns it starting from the second character:


```js
const name = "sam";
const nameCapitalized = name.charAt(0).toUpperCase() + name.slice(1);
```


You can extract that to a function, which also checks if the passed parameter is a string, and returns an empty string if not:


```js
const capitalize = (s) => {
  if (typeof s !== 'string') {
    return '';
  }

  return s.charAt(0).toUpperCase() + s.slice(1)
}

capitalize("sam") // "Sam"
capitalize("s")      // "S"
capitalize(0)        // ""
capitalize({})       // ""
```


Instead of using `s.charAt(0)` you could also use string indexing (not supported in older IE versions): `s[0]`.

Some solutions online advocate for adding the function to the String prototype:

```js
String.prototype.capitalize = function() {
  return this.charAt(0).toUpperCase() + this.slice(1)
}
```

(we use a regular function to make use of `this` - arrow functions would fail in this case, as `this` in `arrow functions` does not reference the current object)


This solution is not ideal, because editing the prototype is not generally recommended, and it’s a much slower solution than having an independent function.

---

Don’t forget that if you just want to capitalize for presentational purposes on a Web Page, CSS might be a better solution, just add a capitalize class to your HTML paragraph and use:

```CSS
p.capitalize {
  text-transform: capitalize;
}
```

---

<!-- Reference -->
[Website]:https://flaviocopes.com/how-to-uppercase-first-letter-javascript/
