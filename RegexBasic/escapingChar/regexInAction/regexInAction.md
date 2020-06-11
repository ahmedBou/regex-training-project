- We've now looked into a bunch of syntax for using regular expressions in Python. Armed with all this knowledge, we can start combining these special characters to create patterns to match the text that we want. For example, say you had a list of all the countries in the world and you want to check which of those names start and end in a. What will the pattern look like? Maybe something like this, A.*a. Let's try that one out.

```python
import re
print(re.search(r'A.*a','Argentina'))
<re.Match object; span=(0, 9), match='Argentina'>
```

- this happened because we didn't specify that we wanted our patterns match the whole string. So while Azerbaijan doesn't finish with A, it does have an A in its name. So it matches our pattern.

```python
import re
print(re.search(r'A.*a','Azerbaijan'))
<re.Match object; span=(0, 9), match='Azerbaija'>
```

-  We need to make our patterns stricter by adding the beginning of a line and end of a line characters.
```python
import re
print(re.search(r'A.*a','Azerbaijan'))
<re.Match object; span=(0, 9), match='Azerbaija'>
```

-  We need to make our patterns stricter by adding the beginning of a line and end of a line characters.

```python
import re
print(re.search(r'A.*a$','Azerbaijan'))
None
```
- Surprising maybe, this happened because we didn't specify that we wanted our patterns match the whole string. So while Azerbaijan doesn't finish with A, it does have an A in its name. So it matches our pattern. We need to make our patterns stricter by adding the beginning of a line and end of a line characters.

- By adding a dollar sign to our pattern, we've made it clear that we only want to match lines that begin and end with the letter a. So Azerbaijan doesn't match anymore. Let's check that it still works for a country that should match like Australia.
  
```python
import re
print(re.search(r'A.*a$','Australia'))
<re.Match object; span=(0, 9), match='Australia'>
```

- Using regular expressions, we can also construct a pattern that would validate if the string is a valid variable name in Python. Do you remember what the rules were? It can contain any number of letters numbers or underscores, but it can't start with a number. So what do you think the validating pattern would look like?
- We said it needs to start with a letter. So we'll start with circumflex to indicate that we wanted to start from the beginning, and now a character class with all lowercase and uppercase letters plus the underscore.
Play video starting at 2 minutes 31 seconds and follow transcript2:31
The rest of the variable can have as many numbers letters or underscores that we want. So we needed another character class this time containing numbers with a star at the end.
Play video starting at 2 minutes 50 seconds and follow transcript2:50
Okay, we're almost done. You definitely deserve a star at the end of this. One last thing, we want this to be the end of the string that we're matching. Otherwise, we could match something that could be a variable, but that also contains additional stuff after it. So we finish up with a dollar sign.

```python
import re
>>> pattern = r"^[a-zA-Z_][a-zA-Z0-9_]*$"
>>> print(re.search(pattern,'_this_is_a_valid_variable_name'))
<re.Match object; span=(0, 30), match='_this_is_a_valid_variable_name'>
```

```python
import re
>>> pattern = r"^[a-zA-Z0-9_]*$"
>>> print(re.search(pattern,'_this_is_a_valid_variable_name'))
<re.Match object; span=(0, 30), match='_this_is_a_valid_variable_name'>
```

- we can use underscores anywhere in the string, that's a valid variable name. It matches our validation pattern because we included underscores in it. Let's try something a little different.

```python
import re
>>> pattern = r"^[a-zA-Z_][a-zA-Z0-9_]*$"
>>> print(re.search(pattern,'this is a valid variable name'))
None
```
- Once we use a space, it stops being a valid variable name. It doesn't matter pattern because spaces aren't included in the possible characters. we can resolve this by adding a space
```python
import re
>>> pattern = r"^[a-zA-Z_][a-zA-Z0-9_ ]*$"
>>> print(re.search(pattern,'this is a valid variable name'))
<re.Match object; span=(0, 29), match='this is a valid variable name'>
```

- Let's check out a variable with a number.
  
```python
import re
>>> pattern = r"^[a-zA-Z_][a-zA-Z0-9_ ]*$"
>>> print(re.search(pattern,'my_variable1'))
<re.Match object; span=(0, 12), match='my_variable1'>
```

- we can use numbers inside the variable name. Our pattern includes all numbers as part of the variable, but what have we start with a number.

```python
import re
pattern = r"^[a-zA-Z_][a-zA-Z0-9_]*$"
print(re.search(pattern,'1my_variable2'))
None
```
- The variable the number at the beginning isn't a valid variable name. In our pattern doesn't match it because the first of two character classes doesn't include numbers.