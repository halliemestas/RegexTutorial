# Regex Tutorial (Regex Tutorial)

In this tutorial, I will take a look into Regex (regular expressions) and how they work. 

## Summary

Regex (short for regular expression) is a string of text that allows you to create search patterns that match, manage, and locate text. An example of regex:

```

/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/

```

* A regular expression used to match a URL

Regex can also be used within a text editor and using command line. 

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

Anchors are characters within the regular expression that allow the user to match strings that begin or ends with a certain character(s). 

Examples of Anchors are as follows:

* `^` - matches any string that start with the anterior word
* `$` - matches a string that end with preceeding word before the character

* Examples:

```

^Hello          matches any string starting with `Hello`

World$          matches any string ending with `World`

^Hello World$   matches exact string

goodbye         matches any string that has the exact text `goodbye` in it

```

### Quantifiers

Qunatifiers are characters within Regex that specify how many instances a character, group, or character class are in the input to be a correct match.

Examples of Quanitifers are as follows:

* `*` - matches a string that has the anterior followed by zero or more of the last character
* `+` - matches a string that has the anterior followed by one or more of the last character
* `?` - matches a string that has the atnerior follwoed by zero or one of the last character
* `{}` -  matches a string that has the anterior followed by how ever many the number in the brackets of the last character in the string
* `()*` - matches a string that has any anterior characters followed by zero or more copies of the string within the brackets

* Examples:

```

abc*        matches a string that has ab followed by zero or more c

abc+        matches a string that has ab followed by one or more c

abc?        matches a string that has ab followed by zero or one c

abc{4}      matches a string that has ac followed by 4 c

abc{3,}     matches a string that has ab followed by 3 or more c

abc{4,2}    matches a string that has ab followed by 4 up to 2 c

a(bc)*      matches a string that has a followed by zero or more copies of the sequence bc

a(bc){2,5}  matches a string that has a followed by 2 up to 5 copies of the sequence bc

```

### OR Operator

OR Operators : if you put the character(s) representing the alternator between any two characters in the regular expression, the result matches the union of the strings that those two characters match.

Examples of OR Operators are as follows:

* `(|)` - matches a string that has any anterior characters followed by the characters on the left or right of alternator
* `[]` - matches a string that has any anterior characters without any characters within the brackets

* Examples: 

```

a(b|c)  matches a string that has a followed by b or c (and captures b or c)

a[bc]   matches a string that has a, but without capturing b or c

```

### Character Classes

Character Classes (Character Set) tells the regex engine to match only one out serveral specific characters, such as digits, words, or whitespace

Examples of Character Classes are as follows:

* `\d` - matches a single character that is a digit
* `\w` - matches a word character (any alphanumeric character plus underscore)
* `\s` - matches a whitespace character (including tabs and line brakes)
* `.` - matches any character
* the capital case for any aformentioned characters will inverse the match

* Examples:

```

\d    matches a single any digit 0-9

\w    matches a single any character that is a-z

\s    matches ` `

.     matches any character

\D    matches a single non-digit character

\W    matches a single any non-character that is a-z

\S    matches a single non-` `

```

### Flags

Flags are optional parameters that add to an expression to make it search in a more specific way. Each flag is denoted by a single character, and serves different purposes in modifying the expression's searching behavior.

Examples of Flags are as follows:

* `g` - Global, does not return after the first match, which restarted any subsequest searches from the end of the previous match (Makes the expression search for all occurences)
* `m` - Multi-line, when enabled the Anchors (^ $) will match the start and end of a line, rather than the whole string
* `i` - Insensitive, makes the entire expression case-insensitive

* Examples:

```

/Hello/g   matches all `Hello` in the test

/Hello/m   matches the beginning and ending of each line with `Hello`, not the whole string `Hello` itself

/Hello/i   matches all `hello` despite case (Hello, hEllo, heLlo, hellO, hello, HELLO all match)

```

### Grouping and Capturing

Grouping unifies a pattern or string so that it is matched in a complete block

Examples of Grouping are as follows:
* `()` - parentheses creates a capture group
* `(?:)` - using `?:` disables the capturing group
* `(?<>)` - using `?<>` puts a name to the group

* Examples:

```

a(bc)           parentheses create a capturing group with value bc

a(?:bc)*        using ?: we disable the capturing group

a(?<bar>bc)     using ?<bar> we put a name to the group

```

### Bracket Expressions

Bracket Expressions are characters enclosed by a bracket `[]` matching any single character within the brackets. 
* `^` signifies any chracter **not** in the list 

Examples of Bracket Expressions are as follows: 
* `[]` - matching any single character within the brackets
* `[]%` - matching the string inside the brackets before the `%`
* `[^]` - matching any string that has not a letter from within the brackets (negation of expression)

* Examples:

```

[abc]         matches a string that etiher has a or a b or a c (same as a|b|c)

[a-c]         similar to case above

[u-zU-Z0-9]   a string that represents a single hexadecimal digit, case insensitively

[0-9]%        a string that has a character from 0-9 before a %

[^a-zA-Z]     a string that has not a letter from a to z or from A to Z

```

### Greedy and Lazy Match

Greedy and/or Lazy Matching are quantifies that expand the match as far as possible through the text. 

Examples of Greedy and/or Lazy Matching are as follows:
* `* + {}` - any one of these character can be used as a quanitifer for a Greedy or Lazy Match

* Examples:

```

<.+?>     matches any character that is one or more times included inside `<` and `>`, and expands as needed.

<[^<>]+>  matches any character expects `<` or `>` one or more times included inside `<` and `>`. 

```

### Boundaries

Boundaries are the places between characters, including spaces. A Boundary should be thought of as a wall between any adjacent characters.
There are two types of Boundaries, **Word** and ***Non-Word**, each denoted by a specific character. 

Examples of Boundaries are as follows:
* `\b` - A position that bounds a word, or where a word starts or ends. It denotes a place between a word and non-word character, at the start and end of a string.
* `\B` - Exact opposite of a word boundary, the negation of `\b` and will match **any position a word boundary doesnt.** *
* `*`Will match between a word and word character, as well as between a non-word and non-word character.

* Examples of Boundaries are as follows:

```

`Hello World` has 12 total Boundaries with 8 Word Boundaries as seen below:
|H|e|l|l|o| |W|o|r|l|d|
^ ^ ^ ^ ^ ^ ^ ^ ^ ^ ^ ^
N W W W W N N W W W W N  -  N = Nonword Boundary \ W = Word Boundary

\babc\b     matches a "whole words only search" for the string `abc`
\Babc\B     matches only if the pattern is fully surrounded by word characters `tabct` would match the string `abc` because it only has word boundaries

```

### Back-references

[Grouping and Capturing](#grouping-and-capturing) can allow you to capture a group to be saved in memory, Back-referencing is the name given to the action of using these matches. 
Back-referencing is the refernce of a captured match, saved in memory, by a captured group.

Examples are a follows:

```

([xyz])\1              using \1 it matches the same text that was matched by the first capturing group

([uwx])([yz])\2\1      we can use \2 (\3, \4, etc.) to identify the same text that was matched by the second (third, fourth, etc.) capturing group

(?<bar>[xzy])\k<bar>   we put the name bar to the group and we reference it later (\k<foo>). The result is the same of the first regex

```

## Author

Hallie Mestas, Junior Developer with the University of Denver

[GitHub Profile](https://github.com/HallieMestas)