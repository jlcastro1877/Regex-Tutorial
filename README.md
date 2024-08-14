# Regex-Tutorial
Tutorial that explains how a specific regular expression, or regex, functions by breaking down each part of the expression and describing what it does

## Summary

### Regex (regular expression) is a sequence of characters that defines a search pattern. It is used for matching and manipulating text based on specific patterns, such as finding, replacing, or validating strings.

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

## Anchors
### /^#?([a-f0-9]{6}|[a-f0-9]{3})$/
### Anchors are a different breed. They do not match any character at all. Instead, they match a position before, after, or between characters. They can be used to “anchor” the regex match at a certain position. The caret ^ matches the position before the first character ###in the string. Applying ^a to abc matches a. ^b does not match abc at all, because the b cannot be matched right after the start of the string, matched by ^. See below for the inside view of the regex engine. Similarly, $ matches right after the last character in the ###string. c$ matches c in abc, while a$ does not match at all.

## Quantifiers
### ^#?([a-f0-9]{6}|[a-f0-9]{3})$/
### Quantifiers are used to communicate how many characters are expected. Quantifiers specify how many instances of a character, group, or character class must be present in the input for a match to be found. By default, quantifiers are greedy, and will match as many ### characters as possible. If the ",+,?,{}" characters are found within regular expressions, they are considered quantifiers. The ? indicates the expression to match 0 or 1time. As mentioned in the summary above because there are 2 types of formats we'll use the or ### operator to distinguish which format we are using. In our Hex Value regular expression we have {6} (Hex Triplet Format) and {3} (Shorthand Hex Format), this indicates that the length of the component preceding these quantifiers should be 6 for {6} and 3 for {3}.

## OR Operator
### /^#?([a-f0-9]{6}|[a-f0-9]{3})$/
### The "or" operator within a regular expression is defined using the | element. The or operator indicates that it could either of the components that we are separating with the |. For our hex value regular expression we have ([a-f0-9]{6}``|``[a-f0-9]{3}). Note the or ### operator separating these 2 components. This means that our hex value could either be 6 characters [a-f0-9]{6} or 3 characters [a-f0-9]{3}.
## Character Classes
### /^#?([a-f0-9]{6}|[a-f0-9]{3})$/
### Character classes are components within our regular expression that tells us what type of characters to expect. In our example our character classes are confined within brackets []. For our example we have 2 character classes: [a-f0-9] and [a-f0-9] which searches ### for the same values. We will be breaking down what the characters are searching within these character classes. a-f searches for letters a-f and 0-9 searches for digits 0-9.

## Flags
### In regular expressions (regex), flags are special characters or settings that modify how the pattern is matched against the input text. Flags can be used to change the behavior of the regex engine, making it case-insensitive, multiline-aware, and more. Here are ### some common flags:
### (case-insensitive): Makes the regex pattern case-insensitive. For example, (?i)abc will match "ABC", "Abc", "aBc", etc.
### (multiline): Changes the behavior of ^ and $ so that they match the start and end of each line within the input, not just the start and end of the entire input. For example, /^abc/m will match "abc" at the beginning of any line in a multiline string.
### (dotall): Allows the dot . to match newline characters as well, so it matches any character including line breaks. For example, /a.b/s will match "a\nb".
### (extended): Allows you to include whitespace and comments in your regex pattern for readability. For example, /a \s+ b/x can be written with spaces and comments for clarity.
### (unicode): Ensures that the pattern is treated as Unicode. This is useful for working with Unicode characters and can affect how certain characters are matched.
### (global): In some languages or tools, this flag allows the regex to find all matches in the input string rather than stopping after the first match. This is commonly used in languages like JavaScript.
### Flags are typically applied at the end of the regex pattern. For instance, in JavaScript, you would use them like this: /pattern/flags. In Python, you use them as parameters in the re.compile() function, like re.compile(r'pattern', re.IGNORECASE)
## Grouping and Capturing
### In regular expressions, grouping and capturing are powerful features that allow you to manage and extract parts of matched text.
### Grouping
### Grouping is done using parentheses (). It allows you to apply quantifiers to part of a regex pattern or to capture specific substrings for later use.
### Examples:
### Basic Grouping: (abc) matches the substring "abc". This doesn't capture it; it's just for grouping.
### Quantifiers with Groups: (abc)+ matches one or more repetitions of "abc" (e.g., "abcabc", "abcabcabc").
### Nested Groups: ((abc)d) groups "abc" and "d" together, which is useful for more complex patterns.
### Capturing
### Capturing is done when you use parentheses () to not only group parts of the regex but also extract the matched substrings. Each group is assigned a capture number starting from 1 (the whole match is capture 0).
### Examples:
### Single Capture Group: (\d{3}) captures three digits. For the input "12345", it captures "123" as group 1.
### Multiple Capture Groups: (\d{3})-(\d{2}) captures two groups: the first three digits and the next two digits. For "123-45", group 1 is "123" and group 2 is "45".
### Non-Capturing Groups
### Sometimes you need to group parts of your regex but don't need to capture them. For this, you use non-capturing groups (?:...).
### Examples:
### Non-Capturing Group: (?:abc)+ matches one or more repetitions of "abc" but does not capture them.
### Named Capturing Groups
### Some regex flavors (like those in Python, JavaScript, and others) allow you to name your capture groups for easier reference.
### Examples:
### Named Capture Group in Python: (?P<area_code>\d{3})-(?P<local_number>\d{4}) captures digits into named groups "area_code" and "local_number".
### python
### Copy code
### import re
### pattern = re.compile(r'(?P<area_code>\d{3})-(?P<local_number>\d{4})')
### match = pattern.match('123-4567')
### print(match.group('area_code'))  # Output: 123
### print(match.group('local_number'))  # Output: 4567
### Named Capture Group in JavaScript: /(?<areaCode>\d{3})-(?<localNumber>\d{4})/ captures digits into named groups "areaCode" and "localNumber".
### javascript
### Copy code
### const pattern = /(?<areaCode>\d{3})-(?<localNumber>\d{4})/;
### const match = pattern.exec('123-4567');
### console.log(match.groups.areaCode);  // Output: 123
### console.log(match.groups.localNumber);  // Output: 4567
### Summary
### Grouping (()) helps with organizing parts of a regex and applying quantifiers.
### Capturing allows you to extract substrings matched by specific groups.
### Non-Capturing Groups ((?:...)) group without capturing.
### Named Capturing Groups make it easier to reference and work with specific captured data.
### These features enhance the flexibility and utility of regular expressions, especially in complex pattern matching and text extraction tasks.
## Bracket Expressions
### /^#?([a-f0-9]{6}|[a-f0-9]{3})$/
### Matches any character in the square brackets. For example [nN] [oO] matches no, nO, No, and NO. gr[ae]y matches both spellings of the word 'grey'; that is, gray and grey.

## Greedy and Lazy Match
### /^#?([a-f0-9]{6}|[a-f0-9]{3})$/
### A greedy match tries to match an element as many times as possible. Whereas, a lazy match tries to match an element as few times as possible. In our example we have ? which signifies lazy quantifier. This is referred to a lazy quantifier because it causes the ### ### regularexpression engine to match as few occurances as possible. We can simply turn this lazy match into a greedy one by adding a ?.
## Boundaries
### In regular expressions, boundaries are special constructs that match positions rather than characters. They are used to assert where matches should occur relative to the positions in the string, such as the start or end of a word or line. Boundaries do not consume ### characters; instead, they assert that a particular condition is met at a given position in the text.
### Here are some common boundary constructs: 
### 1. Word Boundaries: \b and \B
### \b (Word Boundary): Matches the position between a word character (usually [a-zA-Z0-9_]) and a non-word character. It asserts that the position is at the boundary of a word.
### Example:
### regex
### Copy code
### \bword\b
### This regex matches the word "word" only when it is a whole word, not part of another word like "password" or "wording".
### \B (Non-Word Boundary): Matches a position where \b does not match, meaning it asserts that the position is not at a word boundary.
### Example:
### regex
### Copy code
### \Bword\B
### This regex would match "word" only if it is part of a larger word, such as "password" or "swordfish".
### 2. Start and End of Line Boundaries: ^ and $
### ^ (Start of Line): Asserts that the position is at the start of a line or the start of the string (in multiline mode).
### Example:
### regex
### Copy code
### ^start
### This regex matches "start" only if it appears at the beginning of a line or the string.
### $ (End of Line): Asserts that the position is at the end of a line or the end of the string (in multiline mode).
### Example:
### regex
### Copy code
### end$
### This regex matches "end" only if it appears at the end of a line or the string.
### 3. Assertions for Multiline Text
### (?m) (Multiline Mode): Changes the behavior of ^ and $ so that they match the start and end of each line, not just the start and end of the whole string.
### Example:
### regex
### Copy code
### (?m)^start
### With multiline mode enabled, this regex will match "start" at the beginning of each line in a multiline string.
### 4. Lookahead and Lookbehind Assertions
### Positive Lookahead: (?=...) Asserts that a certain condition is true ahead of the current position, without including it in the match.
### Example:
### regex
### Copy code
### \d(?=\D)
### This regex matches a digit only if it is followed by a non-digit character.
### Negative Lookahead: (?!...) Asserts that a certain condition is not true ahead of the current position.
### Example:
### regex
### Copy code
### \d(?!\d)
### This regex matches a digit only if it is not followed by another digit.
### Positive Lookbehind: (?<=...) Asserts that a certain condition is true behind the current position.
### Example:
### regex
### Copy code
### (?<=\d)\D
### This regex matches a non-digit character only if it is preceded by a digit.
### Negative Lookbehind: (?<!...) Asserts that a certain condition is not true behind the current position.
### Example:
### regex
### Copy code
### (?<!\d)\D
### This regex matches a non-digit character only if it is not preceded by a digit.

## Summary
### \b and \B are used for word boundaries and non-word boundaries.
### ^ and $ are used for line start and end boundaries.
### (?m) enables multiline mode for ^ and $.
### Lookaheads ((?=...), (?!...)) and lookbehinds ((?<=...), (?<!...)) are used for asserting conditions ahead or behind a position without consuming characters.
### These boundary constructs are crucial for precise pattern matching and text manipulation, allowing you to control where and how patterns are matched in your input.
## Back-references
### Back-references are typically denoted by \n, where n is the number of the capturing group you want to reference. The numbering starts from 1, based on the order of the opening parentheses in the regex pattern.
## Look-ahead and Look-behind
### Lookahead and Lookbehind are types of lookaround assertions in regular expressions that allow you to assert conditions about the text surrounding a match, without including those surrounding parts in the match itself.
### Lookahead Assertions
### Positive Lookahead ((?=...)): Asserts that a certain pattern must follow the current position in the string, but does not include it in the match.
### Example:
### regex
### Copy code
### \d(?=\D)
### This regex matches a digit (\d) only if it is followed by a non-digit character (\D).
### Negative Lookahead ((?!...)): Asserts that a certain pattern must not follow the current position in the string.
### Example:
### regex
### Copy code
### \d(?!\d)
### This regex matches a digit only if it is not followed by another digit.
### Lookbehind Assertions
### Positive Lookbehind ((?<=...)): Asserts that a certain pattern must precede the current position in the string, but does not include it in the match.
### Example:
### regex
### Copy code
### (?<=\d)\D
### This regex matches a non-digit character (\D) only if it is preceded by a digit (\d).
### Negative Lookbehind ((?<!...)): Asserts that a certain pattern must not precede the current position in the string.
###Example:
### regex
### Copy code
### (?<!\d)\D
### This regex matches a non-digit character only if it is not preceded by a digit.
### Summary

## Lookahead checks for patterns ahead of the current position.
## Lookbehind checks for patterns behind the current position.


## Author
Jorge Castro
### git@github.com:jlcastro1877/Regex-Tutorial.git
