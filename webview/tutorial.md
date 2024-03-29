# Mastering Regular Expressions in JavaScript

Regular expressions, often abbreviated as regex or regexp, are powerful tools used for pattern matching in strings. In JavaScript, regex plays a significant role in string manipulation, validation, and search operations. This guide aims to provide a comprehensive overview of various regex components and techniques, specifically tailored for JavaScript developers.
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

Flags in regular expressions are modifiers that alter the behavior of pattern matching. They are appended after the closing slash of a regex literal in JavaScript (e.g., /pattern/flags). Each flag serves a specific purpose and can change how the regex engine interprets the pattern. Here's an expanded description of common flags:<br/>
<strong><ins>i (case-insensitive):</ins></strong><br/>

When this flag is used, the regex engine ignores the case of letters while performing matches. For example, /hello/i would match "hello", "HELLO", "Hello", etc.<br/>
```javascript
const regex = /hello/i;
console.log(regex.test("Hello")); // true
console.log(regex.test("HELLO")); // true
console.log(regex.test("Hi there")); // false
```
<strong><ins>g (global match):</ins></strong><br/>

This flag enables global matching, meaning the regex engine will find all matches in the input string rather than stopping after the first match. It's particularly useful with methods like String.prototype.matchAll() or when you want to replace all occurrences of a pattern using String.prototype.replace().<br/>

```javascript
const regex = /a/g;
const input = "banana";
let match;
while ((match = regex.exec(input)) !== null) {
  console.log(`Found '${match[0]}' at index ${match.index}`);
}
// Output:
// Found 'a' at index 1
// Found 'a' at index 3
```
<strong><ins>m (multi-line match):</ins></strong><br/>

When the multi-line flag is used, the ^ and $ anchors match the beginning and end of each line in a multi-line string, respectively, rather than the entire string.

```javascript
const regex = /^start/m;
const input = "start\nmiddle\nend";
console.log(regex.test(input)); // true
```


### Grouping and Capturing
Grouping and capturing in regular expressions allow parts of a pattern to be treated as a single unit. They are denoted by parentheses ( ) and can be referenced later in the regex or in replacement strings.

```javascript
const regex = /(apple|banana) pie/;
const match = "apple pie".match(regex);
console.log(match[1]); // apple
```

### Bracket Expressions
Bracket expressions, similar to character classes, match a single character from a specified set. They are denoted by square brackets [ ] and provide more advanced matching options.
```javascript
const regex = /[a-zA-Z]/; // matches any letter
console.log(regex.test("123")); // false
console.log(regex.test("A")); // true
```

### Greedy and Lazy Match

<strong><ins>Greedy Matching:</strong></ins> <br/>
Greedy quantifiers in regular expressions match as much of the string as possible while still allowing the overall pattern to match. They are denoted by symbols such as *, +, ?, and { }. Here's how they behave:<br/>

*: Matches zero or more occurrences of the preceding element. It will match as many occurrences as possible.<br/>
+: Matches one or more occurrences of the preceding element. Like *, it is greedy.<br/>
?: Matches zero or one occurrence of the preceding element. It is also greedy.<br/>
{ }: Matches exactly the specified number of occurrences or within a range. When used without the ? modifier, it is greedy.<br/>
```javascript
const regex = /".*"/; // greedy match
console.log('"cat" sat on the "mat"'.match(regex)); // ["cat" sat on the "mat"]
//It's greedy, so it consumes as much text as possible until it encounters the last " character in the string.
```

<strong><ins>Lazy Matching:</strong></ins> <br/>
Lazy (or non-greedy) quantifiers, denoted by symbols like *?, +?, ??, and { }?, match as little as possible while still allowing the overall pattern to match. They are essentially the opposite of greedy quantifiers. Here's how they work:<br/>

*?: Matches zero or more occurrences of the preceding element, but as few as possible.<br/>
+?: Matches one or more occurrences of the preceding element, but as few as possible.<br/>
??: Matches zero or one occurrence of the preceding element, but as few as possible.<br/>
{ }?: Matches the specified number of occurrences or within a range, but as few as possible.<br/>

```javascript
const lazyRegex = /".*?"/; // lazy match
console.log('"apple" and "banana"'.match(lazyRegex)); // ["apple"]
//Lazy quantifiers match as little as possible while still allowing the overall pattern to match. So, .*? will try to match as few characters as possible.
```
### Boundaries

<strong><ins>\b Boundary:</strong></ins> <br/>
The \b boundary in regular expressions marks the position at the beginning or end of a word. Specifically:<br/>

It asserts a position where a word character (alphanumeric or underscore) is followed or preceded by a non-word character.<br/>
It matches where the word character is at the beginning or end of the string or is adjacent to a non-word character such as space, punctuation, or the start or end of the line.<br/>


```javascript
const regex = /\bapp\b/;
console.log(regex.test("apple")); // true
console.log(regex.test("apple pie")); // false
```

<strong><ins>\B Boundary:</strong></ins> <br/>
The \B boundary is the opposite of \b. It marks the position where a word character is not followed or preceded by another word character. Specifically:<br/>

It asserts a position where a word character (alphanumeric or underscore) is not followed or preceded by a non-word character.<br/>
It matches where the word character is within a word, not at the beginning or end of the string, and is adjacent to other word characters.<br/>
```javascript
const regex = /\Bapp\B/;
console.log(regex.test("apple")); // false
console.log(regex.test("apple pie")); // true
```

### Back-references
Back-references allow referencing previously captured groups within a regex pattern. They are denoted by \ followed by the group number.

```javascript
const regex = /(\d{3})-\1/;
console.log(regex.test("123-123")); // true
console.log(regex.test("123-456")); // false
```


### Look-ahead and Look-behind
<strong><ins>Look-ahead Assertions (?= ):</strong></ins> <br/>
Look-ahead assertions match a group of characters only if they are followed by another pattern, without including the pattern in the match result. Specifically:<br/>

-They are denoted by (?= ).<br/>
-They assert whether a pattern is present immediately after the current position in the string, without consuming any characters.<br/>
-They are useful for checking if a certain pattern exists ahead in the string without including it in the match.


```javascript
const regex = /apple(?= pie)/;
console.log(regex.test("apple pie")); // true
console.log(regex.test("apple juice")); // false
```

<strong><ins>Look-behind Assertions (?<= ):</strong></ins> <br/>
Look-behind assertions match a group of characters only if they are preceded by another pattern, without including the pattern in the match result. Specifically:<br/>

-They are denoted by (?<= ).<br/>
-They assert whether a pattern is present immediately before the current position in the string, without consuming -any characters.<br/>
-They are useful for checking if a certain pattern exists behind in the string without including it in the match.


```javascript
const regex = /(?<=apple )pie/;
console.log(regex.test("apple pie")); // true
console.log(regex.test("banana pie")); // false
```

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
