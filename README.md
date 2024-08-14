# Regex-Tutorial
Tutorial that explains how a specific regular expression, or regex, functions by breaking down each part of the expression and describing what it does
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
###/^#?([a-f0-9]{6}|[a-f0-9]{3})$/
###Anchors are a different breed. They do not match any character at all. Instead, they match a position before, after, or between characters. They can be used to “anchor” the regex match at a certain position. The caret ^ matches the position before the first character ###in the string. Applying ^a to abc matches a. ^b does not match abc at all, because the b cannot be matched right after the start of the string, matched by ^. See below for the inside view of the regex engine. Similarly, $ matches right after the last character in the ###string. c$ matches c in abc, while a$ does not match at all.

### Quantifiers
###^#?([a-f0-9]{6}|[a-f0-9]{3})$/
###Quantifiers are used to communicate how many characters are expected. Quantifiers specify how many instances of a character, group, or character class must be present in the input for a match to be found. By default, quantifiers are greedy, and will match as many ###characters as possible. If the ",+,?,{}" characters are found within regular expressions, they are considered quantifiers. The ? indicates the expression to match 0 or 1time. As mentioned in the summary above because there are 2 types of formats we'll use the or ###operator to distinguish which format we are using. In our Hex Value regular expression we have {6} (Hex Triplet Format) and {3} (Shorthand Hex Format), this indicates that the length of the component preceding these quantifiers should be 6 for {6} and 3 for {3}.
### OR Operator
###/^#?([a-f0-9]{6}|[a-f0-9]{3})$/
###The "or" operator within a regular expression is defined using the | element. The or operator indicates that it could either of the components that we are separating with the |. For our hex value regular expression we have ([a-f0-9]{6}``|``[a-f0-9]{3}). Note the or ###operator separating these 2 components. This means that our hex value could either be 6 characters [a-f0-9]{6} or 3 characters [a-f0-9]{3}.
### Character Classes
###/^#?([a-f0-9]{6}|[a-f0-9]{3})$/
###Character classes are components within our regular expression that tells us what type of characters to expect. In our example our character classes are confined within brackets []. For our example we have 2 character classes: [a-f0-9] and [a-f0-9] which searches for ###the same values. We will be breaking down what the characters are searching within these character classes. a-f searches for letters a-f and 0-9 searches for digits 0-9.
### Flags

### Grouping and Capturing

### Bracket Expressions
###/^#?([a-f0-9]{6}|[a-f0-9]{3})$/
###Matches any character in the square brackets. For example [nN] [oO] matches no, nO, No, and NO. gr[ae]y matches both spellings of the word 'grey'; that is, gray and grey.

### Greedy and Lazy Match
###/^#?([a-f0-9]{6}|[a-f0-9]{3})$/
###A greedy match tries to match an element as many times as possible. Whereas, a lazy match tries to match an element as few times as possible. In our example we have ? which signifies lazy quantifier. This is referred to a lazy quantifier because it causes the regular ###expression engine to match as few occurances as possible. We can simply turn this lazy match into a greedy one by adding a ?.
### Boundaries

### Back-references

### Look-ahead and Look-behind

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
