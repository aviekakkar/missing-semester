## Exercises

1. [RegexOne](https://regexone.com/)

2. Find the number of words (in /usr/share/dict/words) that contain at least three as and don’t have a 's ending. 

	```cat words | awk '$1 ~ /(.*[aA]){3}.*[^sS]$/ {print $1}' | wc -l```

3. What are the three most common last two letters of those words?(sed’s y command, or the tr program, may help you with case insensitivity.) 

4. How many of those two-letter combinations are there? And for a challenge: which combinations do not occur?
