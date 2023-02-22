# Regular Expression: Matching a URL

## Summary

This tutorial will cover how to use Regular Expressions (Regex) to match a URL in web development. We will be exploring a specific regex and breaking down each component to understand what it does. By the end of this tutorial, you will have a solid understanding of this particular regex and how it can be used in your web development projects.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Grouping and Capturing](#grouping-and-capturing)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)

## Regex Components

We will be exploring the `Matching URL` regular expression below: 
```js
/^(https?:\/\/)?([a-z0-9\-]+\.)+[a-z]{2,6}(\/.*)?$/
```
Let's break it down into its individual components and see what each one does:

### Anchors

`^` and `$` are anchors that specify the beginning and end of a line, respectively. In this regex, they ensure that the input string matches the entire pattern, rather than just a portion of it.

### Quantifiers

`+` (one or more) - used to match one or more occurrences of the previous character set or group. For example, 
```js
([a-z0-9\-]+\.)+
``` 
matches one or more occurrences of a group that includes one or more lowercase letters, digits, or hyphens followed by a dot.

`{2,6}` (between 2 and 6) - used to match a specific range of occurrences of the previous character set or group. In this case, it is used to match a group of between 2 and 6 lowercase letters, which represents the top-level domain name (e.g: com, org, edu, etc).

The use of these quantifiers allows the regex to match URLs with varying lengths and components, while ensuring that they adhere to a specific pattern.

### OR Operator

In the regex `/^(https?:\/\/)?([a-z0-9\-]+\.)+[a-z]{2,6}(\/.*)?$/`, the OR operator is represented by the question mark within a set of parentheses: 
```js
(https?:\/\/)?
```
This creates a group that can match either `https` or `http` followed by a colon and two forward slashes. The question mark after `s` makes the `s` optional, so either `http` or `https` can be matched.

This is an example of a non-capturing group, which is used to group together multiple regex tokens but doesn't capture the match for later use in the pattern. In this case, the group is used to match the protocol prefix `http://` or `https://`, but it does not capture this portion of the matched string.

### Character Classes

Character classes are used to define the range of characters that can appear in specific parts of the URL.

The first character class in our regex: 
```js
[a-z0-9\-]+
``` 
matches one or more characters that are either lowercase letters from a to z, digits from 0 to 9, or hyphens (-).

The second character class in our regex: 
```js
[a-z]
``` 
matches a single lowercase letter from a to z.

These character classes are used in the domain name section of the URL to match any combination of letters, digits, and hyphens that form a valid domain name.

### Grouping and Capturing

Within our regular expression, we have 2 groups:
```js
(https?:\/\/)?
```
This is the first group, which is optional due to the ? quantifier. It matches the `http://` or `https://` protocol part of the URL. The `:` and `\/` characters are escaped because they have special meanings in regex syntax. 
```js
([a-z0-9\-]+\.)+
```
This is the second group, which matches one or more subdomains in the URL. It starts with a character class `[a-z0-9\-]` that matches lowercase letters, digits, and hyphens. The `+` quantifier specifies that the previous expression should match one or more times. The `\.` matches the dot between subdomains.

In addition to grouping the sub-expressions, the capturing groups also store the matched sub-strings that can be used later in the regex or in the replacement string in a find-and-replace operation.

### Greedy and Lazy Match

In our regular expression `/^(https?:\/\/)?([a-z0-9\-]+\.)+[a-z]{2,6}(\/.*)?$/`, the greedy and lazy match are represented by the `.*` and `.*?` respectively.

The `.*` is a greedy match that matches any character (except for line breaks) zero or more times. It will match as many characters as possible until it reaches the end of the string or until it encounters a character that prevents it from matching.

On the other hand, the `.*?` is a lazy match that matches any character (except for line breaks) zero or more times. It will match as few characters as possible until it reaches the end of the string or until it encounters a character that requires it to match more characters.

In this particular regex, the `.*` is used to match the path portion of the URL, which may contain any character, while the `.*?` is used to make sure that the optional path portion is matched lazily. This is important because otherwise, the `.*` would match the entire string, including the protocol, domain, and port number, leaving nothing to be matched by the optional path portion.

### Boundaries

The `^` anchor matches the start of the string, and the `$` anchor matches the end of the string. This means that the regex will only match strings that start with the pattern `https://` or `http://`, followed by one or more groups of characters consisting of lowercase letters, numbers, and hyphens, separated by periods, followed by a top-level domain of two to six lowercase letters, and optionally followed by any characters after the domain name.

By using the `^` and `$` anchors, the regex ensures that the entire string matches the specified pattern, preventing partial matches.

## Author

This tutorial is created by Gladys Ange Isingizwe, a web developer passionate about web technologies. You can find more of my work on my [GitHub profile](https://github.com/Isglad).
