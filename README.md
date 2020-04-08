# html-substring
[![Build Status](https://travis-ci.org/bobesa/js-html-substring.svg?branch=master)](https://travis-ci.org/bobesa/js-html-substring)
[![Coverage Status](https://coveralls.io/repos/bobesa/js-html-substring/badge.svg?branch=master)](https://coveralls.io/r/bobesa/js-html-substring?branch=master)

JavaScript code that allows to substring of html content. Only actual text content (no tags, arguments etc.) is counting towards character count.

# Usage
```js
/**
 * Returns html that is stripped to certain character length
 * @param {string} src html content to be stripped
 * @param {number} length max length
 * @param {bool|string=} suffix append dots (or provided string) at the end
 * @returns {string} stripped html
 */
 function html_substr(src, length, suffix){
  //...
 }
```

```js
html_substr("<ul><li>ggg</li><li>mmm</li><li>ccc</li></ul> ddd eee", 5); //Direct use trough prototype
"<ul><li>ggg</li><li>mm…</li></ul>" //Output
```

# Examples
```js
//Typical case
//Single tag is opened and closed (no nesting)
html_substr("<b>Lorem ipsum</b> dolor sit amet, consectetuer adipiscing elit.", 9);
"<b>Lorem ips…</b>" //Output
```

```js
//Nested case
//Multiple open tags at once
html_substr("<b><i>Lorem</i> ipsum</b> dolor sit amet, consectetuer adipiscing elit.", 9);
"<b><i>Lorem</i> ips…</b>" //Output

html_substr("<b><i>Lorem</i> ipsum</b> dolor sit amet, consectetuer adipiscing elit.", 3);
"<b><i>Lor…</i></b>" //Output
```

```js
//Too short case
//In case where you want more characters that is available, whole source string is returned unmodified
html_substr("<b>Lorem ipsum</b> dolor sit amet, consectetuer adipiscing elit.", 99999);
"<b>Lorem ipsum</b> dolor sit amet, consectetuer adipiscing elit." //Output
```

```js
//Custom suffix
//In case you want custom suffix or no suffix, last argument of the function can be boolean or string
html_substr("<b>Lorem ipsum</b> dolor sit amet, consectetuer adipiscing elit.", 5, " cutted");
"<b>Lorem cutted</b>" //Output
```
