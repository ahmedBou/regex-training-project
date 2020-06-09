> wildcard and character classes.

* We've seen by now how we can use a dot in our regular expressions as a special character that can match any character. In the regex world, this is known as a wildcard because it can match more than one character. Using a dot is the broadest possible wildcard because it matches absolutely any character. But what if we wanted something stricter, like checking if an answer given by a user contains a valid character, or finding all the usernames in a CSV file that start with a vowel? We have to restrict our wildcards to a range of characters to do this. 

1. For this task we use another feature of regexes called character classes. Character classes are written inside square brackets and let us list the characters we want to match inside of those brackets. For example, say we want to match the word Python but allow for both lowercase or uppercase p. We could do it like this.
```python
import re
print(re.search(r'[pP]ython', 'Python'))
<re.Match object; span=(0, 6), match='Python'>
```
* Inside the square brackets, we can also define a range of characters using a dash. For example, we could use lowercase a to lowercase z to state any lowercase letter. So if we wanted to look for the string way preceded by any letter, we could write the expression like this one.
```python
import re
print(re.search(r'[a-z]way', 'the end of the highway'))
<re.Match object; span=(18, 22), match='hway'>
```
* The character class defined was matched by the letter H.

```python
import re
print(re.search(r'[a-z]way', 'what a way to go'))
None
print(re.search(r'[ a-z]way', 'what a way to go'))
<re.Match object; span=(6, 10), match=' way'>
```
* We got ***None*** because the string way is preceded by a space and that doesn't match the range that we defined. We can define more ranges like upper case A to upper case Z for all upper case letters or 0 to 9 for all digits. We can combine as many ranges and symbols as we want, like this.
  
```python
import re
print(re.search(r'cloud[a-zA-Z0-9]', 'cloudy'))
<re.Match object; span=(0, 6), match='cloudy'>
print(re.search(r'cloud[a-zA-Z0-9]', 'cloud9'))
<re.Match object; span=(0, 6), match='cloud9'>
```

* we can match anything that's defined between the square brackets.This is super useful. Sometimes we may want to match any characters that aren't in a group. To do that, we use a circumflex inside the square brackets. For example, let's create a search pattern that looks for any characters that's not a letter.
```python
import re
print(re.search(r'[^a-zA-Z]', 'this is a sentence with a spaces'))
<re.Match object; span=(4, 5), match=' '>
```
* our pattern matched the first space in the sentence. What if we also add a space to the list of characters that we don't want to match?
```python
import re
print(re.search(r'[^a-zA-Z ]', 'this is a sentence with a spaces.'))
<re.Match object; span=(32, 33), match='.'>
```
* Because we added a space inside the character class, our example now matched the final dot in the sentence, which isn't in the list of characters to exclude. 
* If we want to match either one expression or another, we can use the pipe symbol to do that. This lets us list alternative options that can get matched. For example, we could have an expression that matches either the word cat or the word dog, like this.
```python
import re
print(re.search(r'cat|dog', 'i like cats'))
<re.Match object; span=(7, 10), match='cat'>
```
* Let's try a sentence with both dogs and cats.
```python
import re
print(re.search(r'cat|dog', 'i like both cat and dog'))
<re.Match object; span=(7, 10), match='cat'>
```
* In this string, we actually have two possible matches for our search. But we only get the first one. That's the way the search function works. 
* If we want to get all possible matches, we can do that using the findall function, which is also provided by the re module, like this.
```python
import re
print(re.findall(r'cat|dog', 'i like both cat and dog'))
['cat', 'dog']
```
* So with findall, we don't need to choose between cats and dogs. we've seen how we can match different groups of characters or even completely different strings.
* Now, what do you think we'd have to do if we wanted to match something more than once? Once you're ready, meet me in the next course to find out.