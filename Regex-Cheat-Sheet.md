# Regular Expression (REGEX) Cheat Sheet

A quick reference guide for common regular expression patterns.

## Basics

- `.` : Matches any character except a newline.
- `\d` : Matches a digit (equivalent to `[0-9]`).
- `\w` : Matches a word character (equivalent to `[a-zA-Z0-9_]`).
- `\s` : Matches a whitespace character (spaces, tabs, newlines).
- `^` : Matches the start of a string.
- `$` : Matches the end of a string.

## Quantifiers

- `*` : Matches 0 or more occurrences.
- `+` : Matches 1 or more occurrences.
- `?` : Matches 0 or 1 occurrence.
- `{n}` : Matches exactly n occurrences.
- `{n,}` : Matches n or more occurrences.
- `{n,m}` : Matches between n and m occurrences.

## Character Classes

- `[abc]` : Matches any character in the set (a, b, or c).
- `[^abc]` : Matches any character not in the set.
- `[a-z]` : Matches any lowercase letter.
- `[A-Z]` : Matches any uppercase letter.
- `[0-9]` : Matches any digit.
- `[\s\S]` : Matches any character, including newlines.

## Anchors

- `\b` : Matches a word boundary.
- `\B` : Matches a position that is not a word boundary.
- `(?=...)` : Positive lookahead assertion.
- `(?!...)` : Negative lookahead assertion.

## Groups and Alternation

- `(abc)` : Capturing group.
- `(?:abc)` : Non-capturing group.
- `|` : Alternation (matches one of multiple patterns).

## Escaped Characters

- `\.` : Matches a period.
- `\\` : Matches a backslash.
- `\(` : Matches an opening parenthesis.
- `\)` : Matches a closing parenthesis.

## Examples

- `\d{3}-\d{2}-\d{4}` : Matches a Social Security Number.
- `^[A-Za-z]+$` : Matches a string of letters.
- `(\d+)\s+([a-zA-Z]+)` : Captures digits followed by letters.

## Flags

Flags are used to modify how the regex is interpreted. They can be added after the closing delimiter.

- `i` : Case-insensitive matching.
- `g` : Global matching (find all matches).
- `m` : Multi-line matching (treats `^` and `$` as line boundaries).

## Resources

- [Regex101](https://regex101.com/): Online regex tester and debugger.
- [Regexr](https://regexr.com/): Another online regex testing tool.
- [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions): MDN's guide to regular expressions.

Remember that different programming languages and tools may have variations in their regex implementations.
