# Regex Tutorial for Matching a URL

A regular expression is a pattern that is matched against a subject string from left to right. Regular expressions are used to replace text within a string, validate forms, extract a substring from a string based on a pattern match, and so much more. The term "regular expression" is a mouthful, so you will usually find the term abbreviated to "regex" or "regexp". This tutorial explains how a regex for matching a URL functions, breaking down each component of the expression and describing what it does.

## Summary

This tutorial describes the regex, or sequence of characters that defines the specific search pattern of a URL, ```/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/```. The characters used in this specific search pattern are called metacharacters, which instead of indicating a literal character, indicates a more generalized pattern. Regex are frequently used to validate input, as when included in code or search algorithms, regex can be used to find certain patterns of characters in a string, or find and replace a character or sequence of characters within a string.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [Grouping and Capturing](#grouping-and-capturing)

## Regex Components

Components of a regex matching a URL include:
* Anchors ```^``` ```$```
* Quantifiers ```*``` ```+``` ```?``` ```{}```
* Bracket expressions ```[]```
* Character classes ```\d``` ```\w``` ```.```
* Grouping and capturing ```()```

### Anchors

The first type is the caret `^` that checks if the matching character is the first character of the input and the second type is the dollar sign `$` which checks if a matching character is the last character of the input string.

In the URL regex, we see two slashes at the start and end, as seen in ```/wlk/```, which flags, or delimits the beginning and end of a regex pattern. We then see ```^``` and ```$``` at those two ends to signify the search pattern found in between those characters.

### Quantifiers

Quantifiers denote the number of characters that belong in the string. ```*``` is a quantifier that matches a string that includes __0 or more__ of the character preceding the ```*``` metacharacter. For example, ```wlk*``` matches a string that has ```wl``` followed by 0 or more ```k```.


```+``` is a quantifier that matches a string that has __1 or more__ of the character preceding the ```+``` metacharacter. ```wlk+``` matches a string that has ```wl``` followed by 1 or more ```k```. 


```?``` is a quantifier that matches a string that has __0 or 1__ of the character preceding ```?``` metacharacter, as in ```wlk?```, which matches a string where ```wl``` is followed by 0 or 1 ```k```. This quanitifier can be found in the first capturing group of the URL regex, ```(https?:\/\/)```, after the "s" character to indicate that the "s" after "http" is optional. It is also found after the first capturing group, ```/^(https?:\/\/)```__?__```([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/```, to denote that the entire first capturing group is optional. Lastly, it is found at the very end of the regex ```/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/```__?__```$/``` to denote the optionally escaped ```/``` at the end of the URL.

```{}``` is a quantifier that matches a string that contains the character preceding the ```{}``` the amount of times delineated in the curled brackets. For example, ```wlk{2}``` matches a string that has ```wl``` followed by 2 ```k```. 

Other ways ```{}``` can be used is with a ```,``` following the number in ```{}```, as in ```wlk{5,}``` which matches a string that has ```wl``` followed by __5 or more__ ```k```. ```wlk{5,10}``` matches a string that has ```wl``` followed by __5 up to 10__ ```k```.

Characters may also be grouped in ```()``` to denote a specific sequence that follows a specific number of times, depending on the quantifier used, as in ```w(lk)*```, which matches a string that has ```w``` followed by __0 or more__ copies of the sequence ```lk```. Used in conjunction with ```{}```, ```w(lk){5,10}``` matches a string that has ```w``` followed by __5 up to 10__ copies of the sequence ```lk```. 

### Bracket expressions

Square brackets are used to specify character sets. Use a hyphen inside a character set to specify the characters' range. The order of the character range inside the square brackets doesn't matter. For example, the regular expression `[Ww]lk` means: an uppercase `W` or lowercase `w`, followed by the letter `l` followed by the letter `k`.

### Character Classes
The character class ```\d``` matches a single character that is a digit, from __0 to 9__. 

The character class ```\w``` matches a single word character which can be __alphanumeric__ or __underscore__.

```.``` matches __any__ character. When escaped with a backslash, as in ```\.```, the regex identifies a literal ```.```.

### Grouping and Capturing

The first capturing group of the URL regex, ```(https?:\/\/)```, includes a pattern that matches an "h", "t, "t", "p", optional "s" character followed by a ":", two escaped "/", and a ```?``` quantifier, indicating 0 or 1 of the preceding capturing group. The URL may or may not include an ```http://``` or ```https://```.

The second capturing group, ```([\da-z\.-]+)```, includes a bracketed character set ```[\da-z\.-]``` which matches any character including a digit character ```\d```, a character from a-z, case-sensitive, an escaped ```.```, and/or ```-```. This character set is followed by the ```+``` quantifier, indicating 1 or more of the preceding character set. This second capturing group is then followed by an escaped ```\.```. The URL includes at least 1 or more of the bracketed character set, followed by a ```.```, as in ```google.``` or ```www.google.``` in  ```www.google.com```.

The third capturing group, ```([a-z\.]{2,6})```, includes a bracketed character set ```[a-z\.]``` which matches any character including an a-z character, case-sensitive, and an escaped ```\.```. This is found 2 and up to 6 times as indicated by the ```{2,6}``` quantifier. Examples of this capturing group include ```.com```, ```.io``` and ```.gov```.

The last capturing group, ```([\/\w \.-]*)``` includes a bracketed character set ```[\/\w \.-]``` which matches any character including an escaped ```\/```, an escaped alphanumeric or underscore word character ```\w```, an escaped ```\.```, and/or ```-``` character. This set is followed by the ```*``` quantifier, indicating a match of 0 or more of the preceding character set. This entire last capturing group is then matched 0 or more times, as indicated by the ```*``` quantifier following the last capturing group, meaning this entire portion of the URL is optional or can have as many additions as delineated.

## Author

Created by Zhongcheng Zhao. For additional questions and information, please go to my [GitHub profile](https://github.com/zhngzh527)
