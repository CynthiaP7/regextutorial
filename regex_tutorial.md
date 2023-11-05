### **Regex Tutorial**

Welcome to the Regex tutorial. This tutorial will help you understand the fundamentals of regular expressions (regex)

### Table of Contents

[Introduction to Regular Expressions](#introduction-to-regular-expressions)
[Anchors](#anchors)
[Quantifiers](#quantifiers)
[Grouping Constructs](#grouping-constructs)
[Bracket Expressions](#bracket-expressions)
[Character Classes](#character-classes)
[The OR Operator](#the-or-operator)
[Flags](#flags)
[Character Escapes](#character-escapes)

### Introduction to Regular Expressions
 The regex to be described is a pattern for validating email addresses. The regex pattern will be explained in detail, and I will provide a code snippet for it.

Regex Pattern for Email Validation: ^(?=.{1,256})(?=.{1,64}@.{1,255}$)(?=.{1,256}\..{1,256}$)(?=.{1,63}\..{1,63}\..{1,63}$)(?=.{1,256}\.\w{2,}$)^[a-zA-Z0-9_](?:(?!\\.$).){0,63}[a-zA-Z0-9]\.[a-zA-Z0-9_]*(?:(?!\\.$).){0,63}[a-zA-Z0-9]$

This regex pattern is designed to validate email addresses. It enforces rules for email format, including overall length restrictions and valid characters. It checks for the correct structure of the local part and the domain part of the email address.

Throughout the tutorial, I will break down each element of this regex and explain how it works. Additionally, I will provide practical examples and tips for using this regex pattern in web development applications.


### Anchors

Anchor tags specify where within a string to apply the search pattern. 

- '`^`' (carat): the search pattern must match at the beginning of the string.
- '`$`' (dollar sign): the search pattern must match at the end of the string.

To provide an example of each in practice using literal characters, let's say we have the following string and search patterns:

```
1. /^Columbia/
2. /Columbia$/
```

In the example provided, which regex would find "Columbia" (#1 or #2)?

The correct answer is #1, as this search pattern specifically looks for the occurrence of "Columbia" at the beginning of the string. To make the string match pattern #2, we could modify it to "Who makes coding fun? Columbia" because "Columbia" appears at the end of the string.

However, in the regex example for email validation, we use the following nomenclature: `/^...$/`, where the search pattern is enclosed between the beginning ^ and ending $ anchor tags. What does this signify?

When you use the beginning `^` and ending `$` anchor tags, it enforces a strict search pattern, requiring an exact match between the string and the search pattern. For example, if we had '/^Columbia$/', it would not match the above example because those anchor tags strictly search for the string "Columbia" without any additional characters.

Therefore, in our email example, the regular expression is strictly enforced to ensure that there are no additional characters before or after the specified search pattern.


### Quantifiers

As the name suggests, quantifiers are important for quantifying (determining the limits of) a regular expression.

Below are some examples of common quantifiers you'll see:

```
* - matches zero or more times of the preceding element. 
+ - matches one or more times of the preceding element.
? - matches zero or one time of the preceding element.
{n} - matches exactly n times
{n,} - matches at least n times
{n,m} - matches between n and m times

```

By nature, quantifiers are **greedy** meaning it will match for as many instances of the pattern there are. To limit the number of occurrences you can add `?` quantifier, which will make the expression **lazy**.

### Grouping Constructs

By placing part of a regular expression inside round brackets or parentheses, you can group that part of the regular expression together. This allows you to apply a quantifier to the entire group or to restrict alternation to part of the regex.

Only parentheses can be used for grouping. Square brackets define a character class, and curly braces are used by a quantifier with specific limits.


### Bracket Expressions

By placing part of a regular expression inside round brackets or parentheses, you can group that part of the regular expression together. This allows you to apply a quantifier to the entire group or to restrict alternation to part of the regex.

'elephant'.match(/[abcd]/) // -> matches 'a'

Only parentheses can be used for grouping. Square brackets define a character class, and curly braces are used by a quantifier with specific limits.


### Character Classes

A character class or character set matches a single character out of several possible characters, consisting of individual characters and/or ranges of characters. A negated character class matches a single character not in the character class. Character class subtraction and intersection allow you to match one character that is present in one set of characters and not/also present in another set of characters.

### The OR Operator

Similar to conditional logic within programming OR Operators give us a way to assess various patterns within the same expression. To use conditional OR operator use `|` symbol.


**Example:**
```
[A-Z]|[0-9]

    Valid matches:
        - ABC
        - 1A3
        - HELLO42
        - 1
```
Essentially any Uppercase Letter (A-Z), Number (btwn 0-9), or any combination would be acceptable. 


### Flags

Flags allow you to change the behavior of a pattern. Think of them as additional rules you can add to your regular expression.

The most common types:

- `i`
    - This stands for case-insensitive. It allows you to pass through a combination of upper and lowercase letters for a string and match regardless of letter case.

- `g`
    - This standards for global. It will search for all instances of the string (not just the first instance).

**Example:**
```
/hello/i

    Valid matches:
        - hello
        - HEllo
        - HellO

/ho/g:
    Valid matches:
      - ho ho ho Merry Christmas
```


### Character Escapes

Escape characters are used to represent special characters (often denoted with a backslash "\").

**Example:**
```
\s -- matches whitespace, tabs, line breaks

    Valid matches:
        - " "
        - Hello There - (space inbetween Hello & There)

\. -- matches period (.) character
     
     Valid matches:
        - google.com
        - cee@gmail.com
        - .

```




