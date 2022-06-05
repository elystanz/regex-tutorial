# Regex for Dummies

Regex, or regular expressions, is similar to a computer, browser, or application's CMD + F or CTRL + F ability to search for words; however, regex is a but more precise in that it can filter a wide variety of characters with great specificity. Are there three Jane Doe's but two have a lowercase D? You can find them with regex! Need to edit any phrase with a `+?` Regex will help you find them quickly with just a bit of input from you!

In this tutorial, we'll go over the regex basics, using a list of names inputted from an example sumbission form.

## Summary

In this short tutorial, you'll be looking at a text list of names. There are a variety of names, with different cases, some with numbers or symbols, and some repeated names but different formats. You will see and understand how regex is used to extract specifics from this list with pictures to help guide you!

Let's look at what we're going to be working with. We are using <a href="https://medium.com/factory-mind/regex-tutorial-a-simple-cheatsheet-by-examples-649dc1c3f285">RegExr</a> to test out our components.

![Regex](https://user-images.githubusercontent.com/95983252/172071135-a3b71447-7730-44c6-93fd-b116e2cb8519.png)

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
Anchors are used at the beginning and end of a regex expression. These anchors are `^` and `$`.

`^` will be used at the beginning to find text that begins with whatever letter, number, symbol, or word you are attaching the anchor to. Here, we are looking for the uppercase D in our list.

![The letter D begin located](https://user-images.githubusercontent.com/95983252/172071589-ec77ee5c-42f7-4594-9c5d-91811e264039.png)

`$` is used at the end of your search, and will look for whatever letter, number, symbol, or word is at the end of a string. Here, we will be looking for words that end with the letter Y.

![The letter Y being located](https://user-images.githubusercontent.com/95983252/172071640-36410701-a4f8-4286-bce3-2c0d777dfb6a.png)


### Quantifiers
Quantifiers match strings with character count. This may seem confusing at first, but check out the following examples that will help clear things up. These quantifiers are writter with symbols `+` `?` `{}` and `*`.

The `+` indicates that we want regex to find text that will match with one or more of a given character. In this next example, we'll insert RY+ into our search. This will be looking for the letter R, followed by one or more of the letter Y. This only happens once in our list, so regex only matches to that instance.

![RY+ being located](https://user-images.githubusercontent.com/95983252/172072077-4f2e0abb-eb6f-4f5f-a607-332abcc45101.png)

Do you see how regex matches with any string with an R, followed by one or more of the letter Y?

<i>As well, you may have noticed that our matches are not case sensitive -- both lowercase and uppercase T's are within this search. We will use character classes to specify case and other parameters later on.</i>

Next, let's look at `?`. This symbol will only find a string that has one or zero of a given letter. Let's stick with RY so you can see the difference. Here, we now will see that the regex search comes back with more than our previous search. This is because it is looking for the letter R followed by one or zero Y's, which regex reads as "R's and RY's only please!"

![RY? being located](https://user-images.githubusercontent.com/95983252/172072147-530195a3-b944-4474-a699-c1f991c56a98.png)

Curly braces, `{}`, are used to find a specifc quantity of characters. In this example, we'll use the letters AN to sort through our list. Let's look for the characters `AN{2}`, with regex searching for one A followed by two N's.

![AN{2} being located](https://user-images.githubusercontent.com/95983252/172072637-60c866d5-5a69-4348-9925-128d6d811c46.png)

Notice how ANN is being matched, but AN is not.

The `*` symbol has a similar functionality to the same symbol in CSS -- it searches for all instances of a letter, number, or word. Here, we are looking for all A's in our list.

[!A's being located](https://user-images.githubusercontent.com/95983252/172072717-64213aa8-f425-46ee-b1a0-552419edd1e8.png)

### OR Operator

OR operators are exactly what the name suggest -- look for this or this. `|` and `[]` are our OR operators.

`|` is used in an expression to find one or another character/string following a word or letter. In this example, we'll look for the letter A followed by either an R or an N.

![A followed by R or N being located](https://user-images.githubusercontent.com/95983252/172072867-1b07e885-b111-4951-908c-dd32bb13249c.png)

The brackets have the same effect.

### Character Classes
Character classes lets us be specific with cases, white space, digits, and non-words. It can be a bit tricky, so definitely head over to <a href="https://medium.com/factory-mind/regex-tutorial-a-simple-cheatsheet-by-examples-649dc1c3f285">RegExr</a> for a bit of practice. They have a 'cheat sheet' full of expressions that can help you navigate your string searches.

Character classes consist of `\w \W`, `\d \D`, `\s \S`, `.` and bracketed expressions.

`\w` looks for a word, while `\W` is the opposite. Similarly, `\d` looks for digits, while `\D` is looking for non-digits. `\s` looks for whitespace, while `\S` looks for all non-whitespace. `.` looks for any character, and brackets allow you to specfiy things like case or letters you do or do not want your search to contain. 

Adding `^` into the start of your search within the brackets is what will cause it to look for anything but what is insert into the brackets, i.e. `[^regex]` will look for anything that does not contain 'regex.'

Below are some examples of character classes in use within our list search.

Here, we can use `\W` to find all non-word characters, which in this case is the white space between these words. As you can imagine, using `\w` will instead highlight the words. Similarly, using `\s` will have the same effect as `\W` here, and `\S` will have the same effect as `\w`.
![\W being used to find all non-word characters](https://user-images.githubusercontent.com/95983252/172073168-82005934-d85e-4d57-897b-d472d942d01e.png)

Now we're using `\d` to find the digits in our list. You can see that only the digits are matched. Alternatively, you can use `\D` to find all non-digits.
![\d being used to find all digit characters](https://user-images.githubusercontent.com/95983252/172073230-8b1f5e47-7e77-4105-93e3-deb08b56dbcc.png)

Using brackets here will allow us to filter certain things, particularly if you're only looking for a certain letter range (maybe you just need to find names P-Z) or a specific casing. Here, we're going to look for letters that range from P-Z, and add the extra oomph of wanting that character to be the start of a string!

![P-Z being located, with that range having to be the first letter of a string](https://user-images.githubusercontent.com/95983252/172073373-9a4ec488-c923-4fbb-a30b-518d84027d8a.png)

If we move the `^` inside of the brackets, regex will then look for all characters that are not within the range of P-Z.

### Flags
Flags are essentially search parameters. You do not have to type these, but you do have to set them. Here you can see the expression flags that allow you to specify parameters that don't need to be written by hand and are just understoof by regex. Here, just global and multiline are selected. You can see in the expression bar that those flags are tacked on at the end.

![Flags](https://user-images.githubusercontent.com/95983252/172073537-2d955068-2a91-4ae6-8fae-3f18f4edb212.png)

Global continues to look for matches even after the first match has been found.

Case insensitive declares to regexs that no matter if A-Z or a-z is in the search expression, it will look for any case.

Multiline will match the start of a line to the end, instead of the entire text (in our case, our list).

Single line (aka dotall) will use . to find new lines.

Unicode will match 32-bit characters, seeing characters as code points instead of code units.

Sticky has regex begin its matching from its index.

### Grouping and Capturing
We've been doing grouping this whole time without realizing! The parenthesis, `()`, allow us to group things and set parameters that reference that group. Here, we can use the Tools section of RegExr to show us what is included within our group.

![RegExr tools section](https://user-images.githubusercontent.com/95983252/172073937-97791818-e862-4112-ba4a-f081d07d1ac1.png)

If you add `?:` to your group, it is disabled, meaning nothing will reference it and it will not be an active search. I.e., `(?:A-Z)`.

You can also name your groups using `?<>` within the parenthesis. This looks something like `(?<first>A-Z)`.

### Bracket Expressions
We have been working with bracket expressions, but just to refresh and dig just a bit deeper, brackets allow us to write in characters or strings to match to our strings. 

Using `[LMAO]` will return a string that has an L, M, A, or O in it. It is the same as our OR operator bracket statement. Similarly, using a hyphen will find a range of letters, such as `[A-Z]`. This can also be used to find numbers!

### Greedy and Lazy Match
`*`, `+`, and `{}` are greedy, meaning they'll look anywhere for a match. Adding a `?` will make it lazy, meaning it won't capture all information, only what it is given. Below, you can see how using `<.+>` returns the div and its contents.

![Greedy match](https://user-images.githubusercontent.com/95983252/172074341-42d4e2e0-c738-47a0-a2a7-e48b6bee2d14.png)

By adding a `?`, we can just grab our divs.

![Lazy match](https://user-images.githubusercontent.com/95983252/172074405-49dba6ee-92c4-40ff-af09-5ff453e65156.png)

### Boundaries
Boundaries are anchor-like elements that allow you to execute a whole word or non-word search. For whole words, we use `\b` and for non-words we use `\B`.

Here, we can see the whole word search in action, looking for the name "Danny"
![\b boundary](https://user-images.githubusercontent.com/95983252/172074509-718df1dc-446d-4a23-82e4-eaec398d4690.png)

### Back-references
Remember when we grouped things up earlier? Back-referencing allows us to use those groups to define search parameters, meaning later groups will look back to the first group to find out if they match the search. Using `\1` allows us to look back to our first group, `\2` to our second, and so forth. Here, let's use an earlier grouping method to check if our second group matches our first. We can use the Tools section in <a href="https://medium.com/factory-mind/regex-tutorial-a-simple-cheatsheet-by-examples-649dc1c3f285">RegExr</a> to check:

![Back-referencing group 2 to group 1](https://user-images.githubusercontent.com/95983252/172074676-2a5c8d84-fe77-4e60-9fc0-bf24bf975153.png)

### Look-ahead and Look-behind
Look-aheads `(?=)` and look-behinds `(?<=)` are used to see if a given character is preceeded or followed by another given character, but that character will not be included in the actual match itself. Let's look for an R, but only if it's followed by an E:

![Locate R followed by E](https://user-images.githubusercontent.com/95983252/172074817-4cc0e492-12ba-446a-ba72-2648ec38dc9c.png)


Now let's find all E's that are preceeded by an N!
![Locate E preceeded by N](https://user-images.githubusercontent.com/95983252/172074820-2aaf9297-7d70-46d6-b113-d1cacb8d978b.png)

## Author
[Elyse Stanziale](https://github.com/elystanz) is a new-to-coding audio engineer based in Nashville. With a passion for art and learning, she's ready to tackle new experiences and aid others who are following similar paths. She hopes this tutorial will be helpful and clear to readers and provide some new insight on how regex works.