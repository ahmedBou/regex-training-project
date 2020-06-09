# Simple Matching With Python

1. we use the re module to apply regular expressions in Python. This module includes a bunch of different functions that can help manipulate strings. 
'''
import re
result = re.search(r'aza', 'plaza')
'''
- We call the search function on the re module, and told it to use the pattern aza on the string plaza. 
We then stored the return value of that function in the result variable. The r at the beginning of the pattern indicates that this is a "Rawstring". 
This means that Python interpreter shouldn't try to interpret any special characters, and instead, should just pass the string to the function as is. 
In this example, there are no special characters. The rawstring and the normal string are exactly the same, but it's a good idea to always use "Rawstrings"
for regular expressions in Python. 

'''
print(result)
<re.Match object; span=(2,5), match='aza'>
'''
- Our result is a match object. The output we get when calling print already shows some interesting information, like the position in the string that matched 
and what the actual matching string was. Let's try this out again with different word.

- What do you think will happen if we pass a string that doesn't match the expression? Let's try and find out.

'''
result = re.search(r'aza', 'maze')
print(result)
None
'''
- If the expression doesn't match the string that we pass, we get none as a result. Remember, none is a special value that Python uses that show that there's
none actual value there.When we're applying regular expressions, we now know that if the search function returns none, it means it didn't find a match.

'''
print(re.search(r"^x", "xenon")
<re.Match object; span=(0,1), match='x'>
'''

2. Here, we told the Storage function to use the circumflex X pattern on the string xenon. We can see that it matched at the beginning of the line
on our X as we expected. What happens if we use a dot which can match any character?

3. What happens if we use a dot which can match any character?
Now we're using p.ng as a search pattern. It matches the word penguin that we're passing. In the match object ,we see the matching string is peng.

'''
print(re.search(r"p.eng", "penguin")
<re.Match object; span=(0,4), match='peng'>
'''
4. We can also pass additional options to the search function. For example, if we want our match to be case insensitive, 
we can do this by passing the """re.IGNORECASE""" option.

'''
print(re.search(r"p.eng", "Pangaea", re.IGNORCASE)
<re.Match object; span=(0,4), match='pang'>
'''

