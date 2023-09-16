# Title (replace with your title)

Introductory paragraph (replace this with your text)

## Summary

A regular expression is a sequence of characters that forms a search pattern. I'll be exolaining the search process in text files - regex pattern can be used to describe what we are searching for. A regular expression can be a single character, or a more complicated pattern. Regular expressions can be used to perform all types of text search and text replace operations. The syntax for regex in Matching an Email or text files: 
/pattern/modifiers; The search() method uses an expression to search for a match, and returns the position of the match.
The replace() method returns a modified string where the pattern is replaced: let ##n = text.search(/name1/i);
Modifiers can be used to perform case-insensitive more global searches:1. i	Perform case-insensitive matching;
2. ##g	Perform a global match (find all matches rather than stopping after the first match) 3.##m	Perform multiline matching
Brackets are used to find a range of characters: 1. ##[abc]	Find any of the characters between the brackets 2. ##[0-9] Find any of the digits between the brackets 3. ##(x|y)	Find any of the alternatives separated with |
Metacharacters are characters with a special meaning:1. ##\d Find a digit 2. ##\s Find a whitespace character  3. ##\b Find a match at the beginning of a word like this: \bWORD, or at the end of a word like this: WORD\b    4. ##\uxxxx	Find the Unicode character specified by the hexadecimal number xxxx and many others




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
Anchors match a position before, after or between characters. The caret, ^ matches the position before the first character in the string, and the dollar symbol, $ matches after the last character of the string. So, like in the snippet above, the ^ and $ basically contain the parameters of the regex.

### Quantifiers
Quantifiers specify how many instances of a character, group, or character class must be present in the input for a match to be found. 
*	*?	Matches zero or more times.
+	+?	Matches one or more times.
?	??	Matches zero or one time.
{ n }	{ n }?	Matches exactly n times.
{ n ,}	{ n ,}?	Matches at least n times.
{ n , m }	{ n , m }?	Matches from n to m times.
The quantities n and m are integer constants. Ordinarily, quantifiers are greedy. They cause the regular expression engine to match as many occurrences of particular patterns as possible. Appending the ? character to a quantifier makes it lazy. It causes the regular expression engine to match as few occurrences as possible. 

### OR Operator
NA for this regex.

### Character Classes
In the context of regular expressions, a character class is a set of characters enclosed within square brackets. It specifies the characters that will successfully match a single character from a given input string. The most basic form of a character class is to simply place a set of characters side-by-side within square brackets. For example, the regular expression [bcr]at will match the words "bat", "cat", or "rat" because it defines a character class (accepting either "b", "c", or "r") as its first character.

### Flags
Regular expressions may have flags that affect the search.

There are only 6 of them in JavaScript:
i - With this flag the search is case-insensitive: no difference between A and a (see the example below).
g - With this flag the search looks for all matches, without it – only the first match is returned.
m - Multiline mode (covered in the chapter Multiline mode of anchors ^ $, flag "m").
s - Enables “dotall” mode, that allows a dot . to match newline character \n (covered in the chapter Character classes).
u - Enables full Unicode support. The flag enables correct processing of surrogate pairs. More about that in the chapter Unicode: flag "u" and class \p{...}.
y “Sticky” mode: searching at the exact position in the text

### Grouping and Capturing
Parenthases are used to group parts of the expression together. In /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/ the username is grouped, then the provider name is grouped, but between them is an @ symbol so nothing affecting those groups affects the @ symbol and the regex will just look for a single @ symbol between those two groups.

### Bracket Expressions
A bracket expression (an expression enclosed in square brackets, "[]" ) is an RE that shall match a specific set of single characters, and may match a specific set of multi-character collating elements, based on the non-empty set of list expressions contained in the bracket expression. 
[abcd]	Matches any character in the square brackets.	
[nN][oO] matches no, nO, No, and NO.
gr[ae]y matches both spellings of the word 'grey'; that is, gray and grey.
[a-d]	Matches any character in the range of characters separated by a hyphen (-).	[0-9] matches any decimal digit.
[ab3-5] matches a, b, 3, 4, and 5.
[0-9]{4} matches any four-digit string.
^[A-Za-z]+$ matches any string that contains only upper or lowercase characters.
\[[0-9 ]*\] matches an opening square bracket, followed by any digits or spaces, followed by a closed bracket.

### Greedy and Lazy Match
By default, quantifiers in regular expressions are greedy, meaning they match as much as possible. However, lazy quantifiers work in the opposite way. They match as little as possible while still allowing the overall pattern to be satisfied. 
Greedy search - to find a match, the regular expression engine uses the following algorithm:
For every position in the string
Try to match the pattern at that position.
If there’s no match, go to the next position.
The lazy mode of quantifiers is an opposite to the greedy mode. It means: “repeat minimal number of times”.
We can enable it by putting a question mark '?' after the quantifier, so that it becomes *? or +? or even ?? for '?'. To make things clear: usually a question mark ? is a quantifier by itself (zero or one), but if added after another quantifier (or even itself) it gets another meaning – it switches the matching mode from greedy to lazy.

### Boundaries
The word boundary \b matches positions where one side is a word character (usually a letter, digit or underscore—but see below for variations across engines) and the other side is not a word character (for instance, it may be the beginning of the string or a space character).
The regex \bcat\b would therefore match cat in a black cat, but it wouldn't match it in catatonic, tomcat or certificate. Removing one of the boundaries, \bcat would match cat in catfish, and cat\b would match cat in tomcat, but not vice-versa. Both, of course, would match cat on its own.

### Back-references
Back-references are regular expression commands which refer to a previous part of the matched regular expression. Back-references are specified with backslash and a single digit (e.g. ' \1 '). Back-references  are used in two cases: in the regular expression search pattern, and in the replacement part of the s command 

### Look-ahead and Look-behind
A regular expression generally matches from left to right. This is why lookahead and lookbehind assertions are called as such — lookahead asserts what's on the right, and lookbehind asserts what's on the left. A lookahead assertion "looks ahead": it attempts to match the subsequent input with the given pattern, but it does not consume any of the input — if the match is successful, the current position in the input stays the same.      (?=pattern) (?!pattern). In order for a (?=pattern) assertion to succeed, the pattern must match the text after the current position, but the current position is not changed. The (?!pattern) form negates the assertion — it succeeds if the pattern does not match at the current position.

## Author

Tetiana Peutona https://github.com/tatiana404
