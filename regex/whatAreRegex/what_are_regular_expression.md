## what are these expressions and why are they regular? 
A regular expression, also known as regex or regexp, is essentially a search query for text that's expressed by string pattern.
When you run a search against a particular piece of text, anything that matches a regular expression pattern you specified, is returned as a result of the search. Regular expressions let you answer the questions like what are all the four-letter words in a file?
Or how many different error types are there in this error log? In other words, regular expressions allow us to search a text for strings
matching a specific pattern.
Knowing about regular expressions can be useful for anyone who needs to perform text processing. From IT specialist to software engineers, 
system administrators and data analyst. 
As a system administrator, I use regular expressions when I need to pull information from a file that has other information in it. 
For example, if I have a file that lists NFS mounts and options and I want to pull only the server name, 
I can write a regular expression that strips each line of the excess data and returns only a list of the information I need.  
For your scripts basic regexs will usually be enough to get you started, and they'll enhance your programs ability to process text. 
We can use command line tools that know how to apply regexs, like grep, sed, or awk. 
We can even use regular expressions inside text processing tools like code or document editors.  
in this training We'll check out how we can apply the regexs to processing, parsing and extracting meaning from texts read by our scripts. 
And we'll look at a bunch of different examples where we can use regular expressions to solve some real world problems. 