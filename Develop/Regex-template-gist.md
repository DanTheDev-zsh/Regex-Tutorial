# Regex Tutorial

    Regular expression (shortened as regex or regexp; sometimes referred to as rational expression) is a sequence of characters that specifies a search pattern in text. Usually such patterns are used by string-searching algorithms for "find" or "find and replace" operations on strings, or for input validation. Regular expression techniques are developed in theoretical computer science and formal language theory. 

<sub>[description source](https://en.wikipedia.org/wiki/Regular_expression)<sub>

## Summary
This gist will cover some of the most commonly used regular expression, they are usually used in conjunction with one another to achieve the programmers goal. 


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
___
### Anchors
Anchors match a position before, after, or between characters. Applying ^a in __abc__ matches a. ^b wants to match letter b at the start of string, but b exists in the middle therefore no match. c$ matches c since the $ anchor matches right after the last character in the string.
___
### Quantifiers
The __"+"__ Quantifier matches between __one__ or __unlimited__ times, as many times as possible, giving back as needed (greedy)  
The __"?"__ Quantifier matches between __zero__ or __one__ times, as many times as possible, giving back needed (greedy)   
The __"*"__ Quantifier matches between __zero__ and __unlimited__ times, as many times as possible, giving back as needed (greedy)   
Applying "/a.*a/g" in the string "greedy can be dangerous at times" will match 8-25 "an be dangerous a". Since it is greedy, it will try to match as many times as possible, to the last occurance of "a".
___
### OR Operator
The | "or" operator matches either what is before the | or what is after it.   
"/cat|dog/g" will match "cat" in the string "My favorite pet would be a British shorthair cat"
___
### Character Classes
Also called the Character Set, allows the regex engine to match only one out of several characters. It is done by inclosing characters you want to match between square brackets "[]".   
"/gr[ae]y/g" will match "gray" or "grey" but will not match graay greey or graey because it will only match exactly one character inside the bracket.
___
### Flags
__g__ flag is commonly used throughout regex, it enables the engine to search for all matches, without it– only the first match is returned.   
__i__ flag is for searching case-insensitively. With it enabled, there is no difference between __A__ and __a__.
__m__ flag is for enabling the multiline mode.   
__s__ flag is for enabling "dotall" mode, that allows a dot __.__ to match newline character "\n".   
__u__ flag is for enabling full Unicode support. The flag enables correct processing of surrogate pairs.   
__y__ flag is for enabling "sticky" mode: searching at the exact position in text.
___
### Grouping and Capturing
A part of a pattern can be enclosed in parenthese (...). This is called a "Capturing group". It allows to get a part of the match as a separate item in the result array, and also allows us to put a quantifier after the parentheses, which applies to the parentheses as a whole.   
An example would be, __go+__ without parentheses will match "goooooooo", while __(go)+__ will match "gogogogogo"
___
### Bracket Expressions
This is similar to Character Classes, which uses the backets "[]".  A character class expression is expressed as a character class name enclosed within bracket- <colon> ( "[:" and ":]" ) delimiters.
__[:lower:]__ will match any lowercase single alphabet character   
__[:upper:]__ will match any uppercase single alphabet character   
___
### Greedy and Lazy Match
Greedy means the engine will try to repeat as many times as possible, and lazy on the other end, will repeat minimal number of times.

Greedy mode was explained in the code snippet part of [Quantifiers](#quantifiers).   
Lazy mode can be enabled by putting a question mark "?" after a quanitfier, so it becomes *?, +?, or even ??. It will try to match least number of times
___
### Boundaries
Boundaries are just like [anchors](#anchors), because it matches at a position.    
An example would be "__\b__", which matches a zero-length.   
Regular Expression __\bis\b__ when used on the string "this is an island" will match only "is" because the boundary specifies that the left and right character is zero-length.   
___
### Back-references
Backreferences match the same text as previously matched by a capturing group.   
Regex "__\b(\w+)\s\1\b__" when applied to "I I am typping typing double double and I don't know why." will match "I I", "typing typing", and "double double".   
The captured group is all individual words, and a space is placed in between the first and backreferenced capture group.
___
### Look-ahead and Look-behind
Collectively called "look-around", are zero-length assertions just like [anchors](#anchors) and [boundaries](#boundaries). The difference is that lookaround actually matches characters, but then gives up the match, returning only the result: match or no match.   
Positive lookahead example: /foo(?=bar)/ applied to "foobar foobaz" will match the first "foo" inside of "foobar" since it is expecting bar to be right after.   
Negative lookahead example: /foo(?!bar)/ applied to "foobar foobaz" will match the "foo" inside of "foobaz" since it is expecting to match "foo" followed not by "bar".   
Positive and Negative lookbehind works the same but the syntax is /(?<=foo)bar/ or /(?<!not )foo/   
___
## Author

Hello, I am Daniel. I'm a new junior web developer who is trying hard to learn the craft, I love low level programming languages such as C++ and python, and I also have a curiousity for [Elixir Programming Language](https://en.wikipedia.org/wiki/Elixir_(programming_language)). Check out my [Github](https://github.com/DanTheDev-zsh?tab=repositories)! 
