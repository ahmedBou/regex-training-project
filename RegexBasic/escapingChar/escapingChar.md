- We've now seen a lot of special characters that we can use in our regular expressions to make them match different kinds of strings: dot, star, plus, question mark, circumflex, dollar sign, and square brackets. But what can we do if we need our pattern to match one of the special characters? Say, for example, that we wanted to check that a certain string contained a dot as part of it. If we just put a dot there, it would match any character.

```python
import re
>>> print(re.search(r'.com', 'welcome'))
<re.Match object; span=(2, 6), match='lcom'>
```
- Here, we wanted to match on strings that had.com in them, but we match a string with something else in it. That's not what we wanted. To match an actual dot, we need to use an Escape character, which in the case of regular expressions is a backslash character. So let's add that to our pattern.
```python
import re
>>> print(re.search(r'\.com', 'welcome'))
None
```

- By escaping the dot, it no longer matched the word Welcome, and since there's no.com in the string, it returned none. Let's try something that should actually match.
  
```python
import re
print(re.search(r'\.com', 'mydomain.com'))
<re.Match object; span=(8, 12), match='.com'>
```
- By adding the backslash, we've got this to correctly match what we wanted it to match. We can use a backslash in this way to escape any special characters, including the ones that we haven't even talked about yet. Something to watch out for. It can get really confusing with backslashes since they're also used to define some special string characters. We've called out, for example, that \n is a sequence using Python to indicate a new line, and \t does the same for tabs. ***When we see a pattern that includes a backslash, it could be escaping a special regex character or a special string character***. Using raw strings, like we've been doing, helps avoid some of these possible confusion because the special characters won't be interpreted when generating the string. They will only be interpreted when parsing the regular expression. On top of this, Python also uses the backslash for a few special sequences that we can use to represent predefined sets of characters. For example, ***\w*** matches any alphanumeric character including letters, numbers, and underscores. Let's check out a couple of examples.
```python
import re
print(re.search(r'\w*','This is an example'))
<re.Match object; span=(0, 4), match='This'>
print(re.search(r'\w*','And_This_is_another'))
<re.Match object; span=(0, 19), match='And_This_is_another'>
```
