# Regex Email Validation Tutorial

Regular expressions (Regex) are patterns using various combinations of characters in strings.

This particular tutorial will be used to match email addresses.

## Summary

This gist will show how regular expressions are used to validate email addresses. An example of this is using characters (a-z)(0-9) and various special characters.

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

These are the characters that are at the beginning and end of the string to be verified. The "^" is regex symbol for this and at the end is the "$" symbol. In an email expression /^([a-z0-9_.-]+)@([\da-z.-]+).([a-z.]{8,12})$/ both the starting and ending anchors have been applied. The first anchor says the start of the string matches the expression. The text [a-zA-Z0-9_.-] can have characters a-z, digits 0-9, and special characters underscore, a dot, or a hyphen. Following the @ symbol tied to the end anchor "$" the end of the string may only contain characters a-z, a dot, and must be between 8 and 12 characters in length.

### Quantifiers

These are characters that determine how often the characters may appear before the quantifier. "?" allow characters to be used only zero or one time. "*" allow characters to be used zero or multiple times. "+" allow characters to be used one or multiple times. "{min, max}" determines that the characters used before a particular symbol must occur at least the "min" number of times and not more than the "max" number of times. In the previous expression /^([a-z0-9_.-]+)@([\da-z.-]+).([a-z.]{8,12})$/, the characters before the "+" quantifer can be used one or more titmes. The {8, 12} are the min and max items in the bracket that must iterate at least eight times to generate eight characters and no more than 12 iterations for 12 characters.

### OR Operator

The "or" operator "|" allows for a choice in matching where the expression matches before or after is acceptable.

### Character Classes

Character classes specify the characters that will successfully match a single character in a given input string. 

- "." represents any characters other than the ones on another line
- "\w" = words
- "\W" = not words
- "\d" = digits
- "\d" = not digits
- "\s" = whitespace
- "\S" = not whitespace
- "[abc]" = a, b, or c
- "[^abc]" = not a, b, or c
- "[a-z] = characters between a and z
The expression /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{8,12})$/ allows for character classes a-z to be used along with "\d" to also include the use of digits. Thus letters a-z and digits 0-9 can be used in the string.

### Flags

There are only six optional Javascript flags that affect searches 
- "i" makes the search case-insensitive so there's no difference between A and a
- "g" makes the search look for all matches, otherwise only the first match is returned
- "m" multiline mode, matches not only at the beginning and the end of the string but also at the start/end of the line
- "s" enables "dotall" mode that allows a dot to match newline character \n
- "u" enables full Unicode support. This flag enables the correct processing of surrogate pairs
- "y" or "sticky" mode: searches at the exact position in the text

### Grouping and Capturing

Each section of a regex pattern is separated by parentheses. This way, quantifiers can be applied to what is inside each of those different sections. In the sample expression /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{8,12})$/ there are three groups, each separated by parentheses. 

### Bracket Expressions

Bracket expressions match a specific set of single characters, and may match a specific set of multi-character collating elemetns, based on the non-empty set of list expressions contained in the bracket expression.

### Greedy and Lazy Match

To find a match with a "greedy" search, for every position in a string, the regex engine algorithm tries to match the pattern at that position. If there is no match, it goes to the next position. On the flip side, the lazy mode means to "repeat minimal number of times."

### Boundaries

\b is a similar anchor to ^ and $ where on side is a word character "\w" and the other side is not.
\B matches all positions where \b does not match.

### Back-references

Match the same text as previously matched text by a capturing group. 

### Look-ahead and Look-behind

Look-ahead asserts that what immediately follows the current position in a string matches the input
Look-behind asserts that what immediately precedes the current position in the string matches the input

## Author

Green horn coder on the rise. https://github.com/nrmoser50/
