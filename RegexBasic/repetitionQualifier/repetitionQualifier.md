- we know how to match one specific character, a group of characters or even any character. Now we're going check out how to match these characters several times. So we wanted to find the longest word in the string, or we wanted to find the host names in a log file by checking for a bunch of alphanumeric characters between brackets. We can do this using another interesting RegEx concept, ***repeated matches***. It's quite common to see expressions that include a ***dot*** followed by a ***star***. This means that it matches any character repeated as many times as possible including zero. Let's see a couple of examples of this.

```python
import re
print(re.search(r'p.*n','python')
<re.Match object; span=(0, 6), match='python'>
```

- with our dot star combination we expanded the range of the match to the whole word. See how the dot takes a different value for each letter? Let's try a different string, Python programming. What do you think the pattern will match?

```python
import re
print(re.search(r'p.*n','python programming'))
<re.Match object; span=(0, 17), match='python programmin'>
```
-  the Star takes as many characters as possible. In programming terms, we say that this behavior is ***greedy***. It's possible to modify the repetition qualifiers to make them less greedy. But we won't get into that now. To learn more about that, check out the next reading. But back to our example. While our pattern could have matched the word Python, it expanded all the way until the last n in the string. If we only wanted our patterns match letters, we should have used the character class instead like this.

```python
import re
print(re.search(r'[a-z]*n','python programming'))
<re.Match object; span=(0, 6), match='python'>
```

- Remember how we said that zero times is also a possibility? That will let the string pin also match our pattern. Let's try that out.

```python
import re
print(re.search(r'[a-z]*n','pyn'))
<re.Match object; span=(0, 3), match='pyn'>
```
- As we called out earlier, implementations of regular expressions aren't always the same. Repetition qualifiers are one way they differ. Some implementations like the one used by grep only include the store qualifier that we just discussed. You can do a lot with just a star qualifier. So that's usually good enough. Other implementations like the one used by Python or by the grep command include two additional repetition qualifiers plus and question mark, that can help us construct more complex expressions. Let's check that out. The plus character matches one or more occurrences of the character that comes before it. So we had the pattern O plus L plus. Let's check it against a few words.

```python
import re
print(re.search(r'o+l+', 'goldfish'))
<re.Match object; span=(1, 3), match='ol'>
```

- In this case, there was one occurrence of each. In the match pattern shows us the shortest possible matching string.
- Here, there were two of each. Again, we can see the match is a whole string that matches the condition. Let's try something that doesn't match.


```python
import re
print(re.search(r'o+l+', 'boil'))
None
```

- So while our string here had an O and an L, it had another character in between them. Because of this, it doesn't match the search pattern. Does that make sense? The question mark symbol is yet another multiplier. It means either zero or one occurrence of the character before it. Let's see how this works.

```python
import re
>>> print(re.search(r'p?each', 'to each their own'))
<re.Match object; span=(3, 7), match='each'>
```
- The P wasn't present but with the question mark we marked it as optional. So we still got a match. Let's see what happens when the P is present.

```python
import re
>>> print(re.search(r'p?each', 'i like peach'))
<re.Match object; span=(7, 12), match='peach'>
```

You just learned about repetition qualifiers, and we saw how there's a bunch of special characters to match different kinds of strings. But what happens when we want to actually match one of those characters like a dollar sign or question mark? Well, lucky for you. We're going to find out in the next .