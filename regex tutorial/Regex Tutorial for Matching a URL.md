# Regex Tutorial for Matching a URL

A regular expression is a pattern that matches an object from left to right. Regular expressions are used to replace text in a string, validate forms, extract a substring from a string based on a pattern match, and much more. The term "regex" is a mouthful, so you'll usually see the expression abbreviated as "regex" or "regexp". This tutorial explains how the URL match regular expression works, breaks down the components of the expression, and describes what it does.## Summary

This tutorial describes the regular expression, or sequence of characters, that defines a specific URL search pattern, ```/^(https?:\/\/)?([\da-z\.-]+)\.( [a-z \.]{2,6})([\/\w \.-]*)*\/?$/```. The characters used in this specific search pattern are called metacharacters, which refer to a more general pattern instead of a literal character. Regular expressions are often used to validate input because when included in code or search algorithms, regular expressions can be used to find certain patterns of characters in a string or to find and replace a character or sequence of characters in a string.
## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [Grouping and Capturing](#grouping-and-capturing)

Regex Components

Components of a regex matching a URL:
* Anchors ```^``` ```$```
* Quantifiers ```*``` ```+``` ```?``` ```{}```
* Bracket expressions ```[]```
* Character classes ```\d``` ```\w``` ```.```
* Grouping and capturing ```()```

Anchors

The first type is the caret `^`, which checks whether the matching character is the first character of the input, and the second type is the dollar sign `$`, which checks whether the matching character is the last character of the input string.

In a URL regular expression, we see two slashes at the beginning and end, as seen in ```/wlk/```, which mark or separate the beginning and end of the regular expression pattern. At these two ends we then see ```^``` and ```$```, which indicates the search pattern found between these characters.

### Quantifiers

Quantifiers indicate the number of characters that belong to a string. ```*``` is a quantifier that matches a string containing __0 or more__ characters preceding the ```*``` metacharacter. For example, ``wlk*'' matches a string that has ``wl'' followed by 0 or more ``k''s.


```+``` is a quantifier that matches a string that has __1 or more__ characters preceding the ```+``` metacharacter. ```wlk+``` matches a string that has ```wl``` followed by 1 or more ```k''`.


```?``` is a quantifier that matches a string that has __0 or 1__ characters preceding the ```?``` metacharacter, as in ```wlk?```, that matches a string where `` After `` wl``` is followed by 0 or 1 ```k```. This quantifier can be found in the first capture group of the URL regular expression, ```(https?:\/\/)```, after the ``s'' character, meaning that the ``s'' after ``http'' is optional. . It is also after the first capture group, ```/^(https?:\/\/)```__?__```([\da-z\.-]+)\.([a-z \. ]{2,6})([\/\w \.-]*)*\/?$/```, which means the entire first scan group is optional. Finally, it is located at the very end of the regular expression ```/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2, 6})( [\/\w \.-]*)*\/```__?__```$/``` to indicate the optional ```/``` character at the end of the URL .

```{}``` is a quantifier that matches a string containing the character preceding ```{}``` as many times as it appears in braces. For example, ``wlk{2}'' matches a string that has ``wl'' followed by 2 ``k''s.

Other ways ```{}''` can be used is with ```,``` after the number in ```{}```, as in ```wlk{5,}```, which matches a string that has ``wl'' followed by __5 or more__ ```k''`. ```wlk{5,10}``` matches a string that has ```wl``` followed by __5 up to 10__ ```k```.

Characters can also be grouped in ```()``` to indicate a specific sequence that follows a certain number of repetitions depending on the quantifier used, as in ```w(lk)*```, which matches a string that has ```w''` followed by __0 or more__ copies of the sequence ```lk''`. When used in conjunction with ```{}```, ```w(lk){5,10}``` matches a string that has ```w''` followed by __5 to 10__ copies of the sequence ``` lk```.

### Expressions in parentheses

Square brackets are used to specify character sets. Use a dash inside a character set to specify a character range. The order of the range of characters in square brackets does not matter. For example, the regular expression "[Ww]lk" means: uppercase "W" or lowercase "w" followed by "l" followed by "k".

### Character classes
The character class ```\d''` matches a single character that is a digit, from __0 to 9__.

The character class ```\w``` corresponds to a single word character, which can be __alphanumeric__ or __underscore__.

```.``` matches __any__ character. When encoded with a backslash, as in ```\.```, the regular expression identifies a literal ```.```.

### Grouping and capturing

The first capture group of the URL regular expression, ```(https?:\/\/)```, contains a pattern that matches the letter ``h'', ``t'', ``t'', ``p'', an optional `` s" character followed by a ":" character, two escaped "/" and a ``?``` quantifier indicating 0 or 1 of the previous capture group. The URL may or may not contain ``http:// ``` or ``https://```.

The second capture group, ```([\da-z\.-]+)```, contains the set of characters in square brackets ```[\da-z\.-]``` that matches any character including numeric character ```\d```, character z a-z, case sensitive, character ```.``` and/or ```-```. This character set is followed by the quantifier ```+``` indicating 1 or more of the previous character set. This second capture group is followed by the character ```\.```. A URL contains at least 1 or more characters in square brackets followed by ```.```, as in ```google.``` or ```www.google.``` in ``` www.google.com```.

The third capture group, ```([a-z\.]{2,6})```, contains the set of characters in square brackets ```[a-z\.]``` that matches any character including a-z, uppercase and lowercase -sensitive and escaped ```\.```. This is found 2 to 6 times, as indicated by the quantifier ```{2,6}```. Examples of this capture group include ``.com'', ``.io'' and ``.gov''.

The last capture group, ```([\/\w \.-]*)``` contains the set of characters in square brackets ```[\/\w \.-]``` that matches any character including escape ```\/```, an alphanumeric or underscore character ```\w```, a ``\.``` character, and/or a ```-``` character. This set is followed by the quantifier ```*``` indicating a match of 0 or more of the previous character set. This entire last capture group is then compared 0 or more times, as indicated by the ```*''` quantifier after the last capture group, meaning that this entire part of the URL is optional or can have as many additions as marked.

