Title

REGULAR EXPRESSIONS - REGEX

Summary

Regular Expressions (Regex) can be used when one is trying to match a certain character combination within a string. Regular expressions are extremely useful in extracting information from any text by searching for one or more matches of a specific search pattern. In this tutorial, I will be using following code to give specific example for how the components of regex can be used. This code can be used to validate an email address that follows correct format.

Matching an Email – /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

Table of Contents

Anchors
Quantifiers
OR Operator
Character Classes
Flags
Grouping and Capturing
Bracket Expressions
Greedy and Lazy Match
Boundaries
Back-references
Look-ahead and Look-behind
Regex Components

Anchors

Anchors are denoted by ^ and $

Anchors are regex components that start and ends a srting.

For example,

^Good - matches any string that starts with Good
morning$ - matches a string that ends with morning
^Good morning$ - exact string match that starts and ends with Good morning
play - matches any string that has the text play in it
Let us now demonsterate how anchor works in case of our matching email code

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`
The anchor ^ and $ demonstrates that the code must start with ^([a-z0-9_\.-]+) and end with .([a-z\.]{2,6})$

In order to be valid it must start and end with the given parameters within the code. If it does not, then it is not a match.

Quantifiers

Quantifiers are denotaed by * + ? and {}

A quantifier is used to determine how many times a specific character or group of characters needs to be present in order to have a match.

* Matches 0 or more occurrences of the element that precedes it.
+ Matches 1 or more occurrences of the element it follows.
? Matches 0 or 1 occurrences of the element it follows.
For example,

abc* - matches a string that has ab followed by zero or more c
abc+ - matches a string that has ab followed by one or more c
abc{2} - matches a string that has ab followed by 2 c
abc{2,5} - matches a string that has ab followed by 2 up to 5 c
So, if we look at our code for matching the email:

([a-z0-9_\.-]+)

this will match any string that contains a-z, 0-9, _, ., or -. The quantifier + means that it has to contain at least one of this in order to have a match.

OR Operator |

You can use the | operator (logical OR) to match characters or expression of either the left or right of the | operator. For example: couch|chair finds couch or chair.

OR operator is not present in our email code /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

Consider a hex regex code for example /^#?([a-f0-9]{6}|[a-f0-9]{3})$/ Let's breakdown the code and look what each part states.

It starts with #
Match a 6 character long string that contains a combination of a-f letters and 0-9 numbers [a-f0-9]{6}
OR Operator |
Match a 3 character long string that contains a combination of a-f letters and 0-9 numbers [a-f0-9]{3}
Character Classes

A character class is a set of characters enclosed within square brackets. It specifies the characters that will successfully match a single character from a given input string. For example,

\d - matches a single character that is a digit between 0 to 9
\w - matches a word character [A-Za-z0-9_]
\s - matches a whitespace character
\D - matches a NON-digit character
In our exapmle code,/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

\d represents a single digit ranging from 0 to 9 after @ sign in email address. It will only match a single digit such as "5", but not "55".

Flags

A flag is an optional parameter to a regex that modifies its behavior of searching. A flag changes the default searching behaviour of a regular expression. It makes a regex search in a different way. A flag is denoted using a single lowercase alphabetic character.

For example,

i - Ignore Casing - Makes the expression search case-insensitively.
g - Global - Makes the expression search for all occurrences.
s - Dot All- Makes the wild character . match newlines as well.
m - Multiline- Makes the boundary characters ^ and $ match the beginning and ending of every single line instead of the beginning and ending of the whole string.
y - Sticky- Makes the expression start its searching from the index indicated in its lastIndex property.
u - Unicode- Makes the expression assume individual characters as code points, not code units, and thus match 32-bit characters as well.
In our email address regex code there are no flags. /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

Grouping and Capturing

Capturing groups are a way to treat multiple characters as a single unit. They are created by placing the characters to be grouped inside a set of parentheses. For example,

z(yz) - parentheses create a capturing group with value yz Consider our email address code, /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

([a-z0-9_\.-]+) is the first group that appears in our regex that matches the user email name.

([\da-z\.-]+) is the second group that appears in our regex which will match the email service.

([a-z\.]{2,6}) is the third group that appears in our regex that capture the domain's .com.

Bracket Expressions []

A bracket expression (an expression enclosed in square brackets, "[]" ) is regex that shall match a specific set of single characters, and may match a specific set of multi-character collating elements, based on the non-empty set of list expressions contained in the bracket expression.

Bracked expressios for email validation includes the following character sets: /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

[a-z0-9_\.-] which is matching any letter a-z and is case senstive. It also matches a character 0-9 and matches the characters "_" , "-" , and "."
[\da-z\.-] which is matching a single digit from 0-9, any character a-z (case senstive), and the characters "." and "-".
[a-z\.] matches any character a-z(case senstive) and the character ".".
Greedy and Lazy Match

Greedy means match longest possible string. Lazy means match shortest possible string.

The quantifiers ( * + {}) are greedy operators, so they expand the match as far as they can through the provided text.

our email address, /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/ includes the + Quantifier, it will match as many times as possible giving back as needed. Another greedy Quantifier used in this regex is {} when matching {2,6}for the last capture group.

Boundaries

The (\b) is an anchor like the caret (^) and the dollar sign ($). It matches a position that is called a “word boundary”. The word boundary match is zero-length.

The following three positions are qualified as word boundaries:

Before the first character in a string if the first character is a word character.
After the last character in a string if the last character is a word character.
Between two characters in a string if one is a word character and the other is not.
Boundaries are not used in the given matching an email code. /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

Back-references

Backreferences match the same text as previously matched by a capturing group For example, ([abc])\1 using \1 it matches the same text that was matched by the first capturing group

Back-references are not included in the given code. /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

Look-ahead and Look-behind

(?=) and (?<=)

(?=foo) Lookahead Asserts that what immediately follows the current position in the string is foo.

(?<=foo) Lookbehind Asserts that what immediately precedes the current position in the string is foo.

It is not being used in the given matching an email code. /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

Author

Jasmine Virk is a Junior Developer towards the end of his coding bootcamp through University of Toronto.

Feel free to check out his GitHub repo for all of his previous projects

https://github.com/jvirk10