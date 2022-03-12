---
title: Sortest Word
published: true
---

Code Wars is a great site for keep your programing skills sharp no matter what language you are learning or well versed in. It's not every day that you have something to code, at least I don't. Code Wars gives you a challenge and you earn reputation points. This post is a writeup of how I completed the Shortest Word challenge. We are first given our clue and the initial function code.

```python
# Simple, given a string of words, return the
# length of the shortest word(s). String will
# never be empty and you do not need to account
# for different data types.


def find_short(s):
    # your code here
```
First thing we need to do is figure out our steps for getting python to do what we need it to.

- [ ] Variable to hold a string
- [ ] Strip the string of anything nefarious (symbols and numbers)
- [ ] Make a way for python to see each word in the string individually
- [ ] Count the words and find the shortest one
- [ ] Return the shortest word

Making the variable `s` for the string and strip it of unhelp characters is simple.
What we do in the below code is preform a for loop defining `char` (characters) that we need removed.

Next we redefine our `s` variable and replace any of the characters we found (stored in the char variable) with a blank space. Now redefine the s variable again making all the words lowercase.

```python
s = "This is a string of words"

def find_short(s):
    for char in '-.,0123456789\n':
		s = s.replace(char, ' ')
	s = s.lower()
```

To make the code easy for python to count we will put the cleaned sting in a list (named words) with each word as one item in the list.

```python
words = list(s.split(" "))
```

If you printed words it would look like this like the code below.

```python
# our origional string
# s = "This is a string of words"

words = ['this', 'is', 'a', 'string', 'of', 'words']
```

To get python to count the number of characters in each word  we will create another for loop with an if statement nested in it. The for loop cycles through each item in our words list counting it's length and testing them against our if statement condition looking for the shortest word and when a word meets our condition it gets stored in variable l.  

We then printing the l variable and put a return of the same variable to satisfy Code Wars' conditions.  
```python
for word in words:
		if len(word) < 1:
		l = len(word[0])
	print(l)

    return l # l: shortest word length
```

There you have it! Not too bad, the one part that gave me trouble was cleaning up the string. I had not seen the replace tool before and it took me some research to find it. Looking back on the code as I write this there are a few ways I could clean this up and even expand it to deal with multiple *shortest* words (ie s = "Get Bet But Bot Boo"). There are also ways someone could cheat the system by just adding shorthand or false words (Cali instead of California).