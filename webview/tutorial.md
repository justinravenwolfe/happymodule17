# Title (replace with your title)

Introductory paragraph (replace this with your text)

## Summary

Briefly summarize the regex you will be describing and what you will explain. Include a code snippet of the regex. Replace this text with your summary.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components
 

### Anchors
Anchors in regular expressions are used to specify the position of a match within the string. The ^ anchor matches the start of a string, while the $ anchor matches the end of a string. Additionally, \b matches a word boundary, and \B matches a non-word boundary.

```javascript
  const regex = /^start/;
  console.log(regex.test("start of the string")); // true
  console.log(regex.test("at the start of the string")); // false
```


### Quantifiers
Quantifiers define the number of occurrences of a character or a group in a regex pattern. Common quantifiers include :<br />
  (1) * (zero or more occurrences).<br />
  (2) + (one or more occurrences).<br />
  (3) ? (zero or one occurrence).<br />
  (4) {n} (exactly n occurrences).<br />
  (5) {n,} (at least n occurrences).<br />
  (6) {n,m} (between n and m occurrences).<br />

```javascript
const regex = /a+/;
console.log(regex.test("aa")); // true
console.log(regex.test("b")); // false
```

### OR Operator

  The OR operator, denoted by |, allows specifying multiple alternatives in a regex pattern. It matches either the expression before or after it.

```javascript
const regex = /apple|banana/;
console.log(regex.test("apple pie")); // true
console.log(regex.test("banana split")); // true
console.log(regex.test("cherry pie")); // false
```



### Character Classes

Character classes in regular expressions are powerful tools for matching specific sets of characters within a string. They are denoted by square brackets [ ] and provide a flexible way to define which characters you want to match. Here's an expanded explanation of the features of character classes: <br />

<strong>Single Characters:</strong> Inside a character class, you can specify single characters that you want to match exactly. For example, [abc] matches either 'a', 'b', or 'c'. <br />

<strong>Ranges:</strong> You can define a range of characters using a hyphen - inside the brackets. For instance, [a-z] matches any lowercase letter from 'a' to 'z'. Similarly, [0-9] matches any digit. <br />

<strong>Negation:</strong> If you prepend a caret ^ inside the brackets, it negates the character class. This means it matches any character that is not listed inside the brackets. For example, [^0-9] matches any character that is not a digit. <br />

<strong>Shorthand Notations:</strong> Regular expressions provide shorthand notations for common character classes:<br />

<strong>\d:</strong> Matches any digit character. Equivalent to [0-9].<br />
<strong>\D:</strong> Matches any non-digit character. Equivalent to [^0-9].<br />
<strong>\w:</strong> Matches any word character (alphanumeric character plus underscore). Equivalent to [a-zA-Z0-9_].<br />
<strong>\W:</strong> Matches any non-word character. Equivalent to [^a-zA-Z0-9_].<br />
<strong>\s:</strong> Matches any whitespace character (space, tab, newline, etc.).<br />
<strong>\S:</strong> Matches any non-whitespace character.<br />


```javascript
const regex = /[a-zA-Z0-9]/; // Matches any alphanumeric character
console.log(regex.test("Hello123")); // true
console.log(regex.test("@#$%")); // false
```

```javascript
const regex = /[aeiou]/;
console.log(regex.test("apple")); // true
console.log(regex.test("banana")); // true
console.log(regex.test("cherry")); // false
```



### Flags

### Grouping and Capturing

### Bracket Expressions

### Greedy and Lazy Match

### Boundaries

### Back-references

### Look-ahead and Look-behind

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
