# 17 Regex Tutorial

This is the gist of the challenge

## Summary

 I will be describing the "Matching an Email" regex, or regular expression, as shown here: /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/ A matching email regex would be used to validate an email address. For example, if a user is filling out a form online or answering an inquirer prompt in a node.js program, this regex could be used to make sure they enter an email address when asked for one. Essentially, a regex is defining a search pattern.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)

## Regex Components

### Anchors

Anchors match a position before, after or between characters. The caret, ^ matches the position before the first character in the string, and the dollar symbol, $ matches after the last character of the string. So, like in the snippet above, the ^ and $ basically contain the parameters of the regex.
### Quantifiers

Quantifiers specify how many instances of a character, group, or character class must be present for a match to be found. So, for a regex that is meant to match an email address, you'd want to use the plus sign, +, operator. The + on it's own is known as a greedy operator, as it will match as many occurances as possible. In [a-z0-9_\.-]+@ from our email matching regex, the expression will look for at least one or more instances of everything in the brackets: "lowercase a through z" and/or of "zero through nine" a period (the backslash lets the regex interpret the period as a literal period by "escaping" it), and a dash. After the + is the @ so it will stop this part of the search once it gets to the @.

The {2,6} at the end will looks for a range of 2-6 characters. Which works for an email address because they end in something like .com or .net which is between 2 and 6 characters long.
### Grouping Constructs

Parenthases are used to group parts of the expression together. In /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/ the username is grouped, then the provider name is grouped, but between them is an @ symbol so nothing affecting those groups affects the @ symbol and the regex will just look for a single @ symbol between those two groups.
### Bracket Expressions

Using brackets allows a regex to match specific characters in a range. So, [a-z] is not looking for a or - or z, but actually looking for any letters a through z. And in the brackets the "-" is not taken literally in the cases of a-z or 0-9. But after the \ to escape the period it is recognized as a literal "-".
### Character Classes

The \d used in the email matching regex is looking for any single digit. Since it is wrapped in brackets followed by the + sign, it can be one or more digits If it was just on its own it would only allow a single digit, or something like \d\d\d that would mean only three digits.
### The OR Operator

The purpose of an OR operator is to match the characters on the left or right of the operator, essentially serving as an or, as in and/or. Using the | as in m|M would match either m or an M from the string. If we had used https?:\/\/(www\.)?[\d-a|A it would search or a OR A.

### Flags

Flags are used at the end of a regex, after a closing slash. They are tokens that will modify parameters of a search. Multiple flags can be set by writing one after another with NO spaces. Flags must be written in lowercase. This URL does not contain any flags. An example of a flag would be if the above expression showed: (shows global expression. See below)

https?:\/\/(www\.)?[\d-a-zA-Z0-9@:%._\+~#=]{1,256}\.[a-zA-Z0-9()]{1,6}\b([-a-zA-Z0-9()@:%_\+.~#?&//=]*)g
Flag Expressions:

i: Ignores casing. Makes expression case-sensitive
g: Global. Makes expression search for all occurences
s: Dot All. Makes the wild characters . match newlines as well
m: Multiline. Makes boudnary characters ^ and $ match beginning and end of every line.
y: Sticky. Indicates that it matches only from the index indicated by the lastIndex property of this regular expression in the target string (and does not attempt to match from any later indexes)
u: Unicode. Expression assumes individual characters are code points, not code units and will then match 32 bit characters.
### Character Escapes

The backslash in a regular expression precedes a literal character. You also escape certain letters that represent common character classes, such as \w for a word character or \s for a space. The following example matches word characters (alphanumeric and underscores) and spaces.

Regex(
	"Are you there, Alice?, asked Jerry.", // source
	"(here|there).+(\w+).+(said|asked)(\s)(\w+)\." ); // regular expression
"there, Alice?, asked Jerry."
## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
