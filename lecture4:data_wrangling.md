## Solutions 

1. [RegexOne](https://regexone.com/)

2. Find the number of words (in /usr/share/dict/words) that contain at least three as and don’t have a 's ending. 

```bash
cat words | awk '$1 ~ /(.*[aA]){3}.*[^sS]$/ {print $1}' | wc -l
```

3. What are the three most common last two letters of those words?(sed’s y command, or the tr program, may help you with case insensitivity.) 
	
	a.  `al`
	b.  `an`
	c.  `ae'

4. How many of those two-letter combinations are there? And for a challenge: which combinations do not occur?

```zsh  
cat words | awk '$1 ~ /(.*[aA]){3}.*[^sS]$/ {print $1}' | sed -E 's/.*(..)/\1/' | sort | uniq -c | sort -k1,1 | tail -n3 
```

_PS: the first `sort` must preceed `uniq -c` as uniq only compares __adjacent lines__._

5. To do in-place substitution it is quite tempting to do something like sed s/REGEX/SUBSTITUTION/ input.txt > input.txt. However this is a bad idea, why? Is this particular to sed? Use man sed to find out how to accomplish this.

	This is a bad idea as one risks corruption or partial content in situations where disk space is exhausted, etc. 

	To accomplish the same use the `-I or -i` extension making sure to provide a non-zero extension. (e.g, sed -i .md `s/REGEX/SUBSTITUTION` ) 


