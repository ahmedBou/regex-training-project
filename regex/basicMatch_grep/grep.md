> Grep
1. Grep is an especially easy to use yet extremely powerful tool for applying regexes. It's a great way to easily try out some expressions and get 
familiar with them. So let's look at some basic matching we can do with grep.The simplest of all matchings is just to search to see if the string is present. 
Remember, that grep works by printing out any line that matches the query that we pass it. So for a simplest query of passing a plain old string, 
grep will print any lines containing that string in the file that we give it. Let's try this out using grep to find words inside a file.

* grep <word> <file>

* So when we call grep with <word> as a pattern to match on and we pass our list of words as a file, we see that it matches with a bunch
of different words.These words, all contain the string <word> somewhere inside of them, which is why they appear in our results. 
* We also see that the output is highlighted for us, showing us the matching part of the line in a different color. 
This added visual indicator is something that grep does for us so that we can easily see where the match occurred. 
It's worth calling out that the string we're passing in grep is case sensitive. So it needs to be matched exactly. 
If we use uppercase letters, they'll only be matched by uppercase letters. If we wanted to match a string regardless of case, 
we will have to pass the -i parameter to the grep command, like this.

* grep <word> -i <file>


* So we now know that any basic string is already a regular expression which will match a line that contains that string. 
To get the most out of regular expressions, we need to learn more of their syntax, which can be as complicated as it is powerful. 
In particular, we have to know the reserved characters that give extra meaning to the patterns that we create. It's these characters that allow us to do more advanced matching than just checking for a literal string. 
For example, a dot matches any character. This means that if we include

2. a dot in our expression, that dot is a wildcard that can be replaced by any other character in the results. Let's check out an example of this.

```
grep l.rts <file>
alerts
blurts
flirts
```
* Here, we're looking for the pattern l.RTS within the list of words. This pattern matches three different words; 
alerts, blurts, and flirts. Check out how for each of those words, the dot in our pattern was substituted by different letter. 
we can find portions of texts that match a given pattern even when the pattern isn't a whole word. We could use this, for example, 
to look for entries in a log file that match a certain format or to find rows in a CSV file that share the same characteristics even 
if they are not exactly the same. Other easy examples of special characters that we can use in a irregular expressions are the caret, or circumflex and the dollar sign anchor characters. 
These tell us where in the line the regex should match from. The circumflex indicates the beginning and the dollar sign indicates the end of the line. For example, to look for all the words that.
start with a string fruit, we would write grep circumflex fruit in our file.

* grep ^fruit <file>

* We'll use grep to find all the words that end with cat by writing grep cat dollar sign into our file.

grep cat$ <file>


One thing to remember is that the circumflex and the dollar sign specifically match the start and end of the line, not a string. 
Take a log file for example, where each line contains a lot of different words. We can use a circumflex to check if a line begins with a pattern or use a dollar sign and check if it ends with a pattern, but our patterns will match only if the line fits that criteria, not the contained words.