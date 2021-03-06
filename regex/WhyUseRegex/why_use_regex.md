> Why use regex
1. you might be wondering why do I need more processing power than just looking for strings in a text which I already know how to do in Python? 
The answer lies in the power and flexibility of regular expressions. For example, let's say we have log entries with a typical log line format like this one.
```python
log = "July 31 07:51:48 mycomputer bad_process[12345]: ERROR Performing package upgrade"
```
* We want to extract the process identifier from this line, which is a number between the square brackets 12345. 
There's a lot of extra text in this log line that we don't need, like the date, the computer name and other info. 
We could extract the process ID by using the index method to find the first square bracket in the string. 
```python
index = log.index("[")
```

* Remember that when accessing strings, the index of the character is the position of that character in the string starting from 0.
In this example, the index of the first square bracket would be 39. If we don't want to capture the square brackets, 
we will start at the next version and include five more characters after that. Let's give it a go.
```python
print(log[index+1:index+6])
12345
```

* we get the text that we wanted, we might hit a few bumps down the road. Can you spot them? 
One problem is we don't know for sure how long the process ID string will be in all cases. 
In this example, we can see that it's five characters long. But that may change in the future if the computers restarted, 
or the number of processes increases. This could also break if for any reason, the line includes another square bracket before the process ID. 
So it's a solution but it's a very brittle one. Any other ideas? Instead, we could use a regular expression to extract the process ID in a more robust
fashion. For that, we're going to import the RE module, which lets us use the search function to find regular expressions inside strings.
```python
import re
```

* this regular expression will work no matter where our process ID shows up or how long or short the line is. 
As long as there's a single sequence of numbers in the string marked by square brackets, this regex will extract those numbers for us. 
If the regular expressions stored in the regex variable looks like gibberish at this point, don't worry, that's expected. 
We'll explore syntax and how we use these expressions in upcoming videos. 
At this point, the key takeaway is that regular expressions are both powerful and flexible tools. 
By the end of this module, you'll be able to read and unpack statements like the one in this example, 
we're off to a strong start. Next stop, we'll learn how to use some very basic matching with the grep command.