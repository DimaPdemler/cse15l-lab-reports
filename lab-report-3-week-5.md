Dmitri Demler
  
A16992026
  
CSE 15L
# Lab Report 3

## Command: Less

By itself the command **less** opens a user defined file in a seperate terminal window helping keeping the original terminal window clean and organized. You can leave the window by pressing Q.
  
````
less -p[pattern] <file>
````
This command opens the file as before but highlights the pattern you typed in the command. This is helpful if you are looking for a spciefic word in a document: 
  
Example:
````less -pcell biomed/rr166.txt````

![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/labreport3image2.jpg)

You can also use patterns in the built in window to find various words. This accomplishes a similar purpose but you can change what word to search while viewing: ````/[pattern]````

````
less biomed/rr166.txt
/cell 
````

![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/labreport3image5.jpg)

You can only view the lines that contain the pattern by doing ```` &[pattern]````

````
less -N  biomed/rr166.txt
&cell
````
![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/labreport3image6.jpg)

## Command: grep
  


Typically, **grep** is used to find a string in a document. However, by using **-e**, you can specifiy a specific pattern to look for. This gets even more powerful with the combination of other commands:

````
grep -e [pattern] [file]
````

Example 1: ````grep -e the biomed/rr167.txt ````

![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/labreport3image8.jpg)

Example 2: ```` grep -v -e 'the' -e 'a' biomed/rr167.txt````

Here the terminal looks for all lines that dont contain 'the' or 'a'. The pattern here is 'the' and 'a' and **-v** looks for the inverse pattern.

![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/labreport3image9.jpg)

Example 3: ```` grep --color=always -r -e 'the'  biomed/ | grep --color=always 'fish'````

This recursively looks in the folder biomed for lines that contain both 'fish' and 'the'.

![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/labreport3image10.jpg)


## Command: find

**Find** "walks" in a file directory to find a specific file or files that you are looking for. Adding **-size** searches for files of a given size. 

````
find [directory] -size [param]
````

Example 1: ````  find ./*/* -size +10k ````
  
This finds the files that are larger than 10 kilobytes. 

![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/labreport3image11.jpg)

Example 2: ````find ./*/* -size +10k -size -20k ````

This finds the files in technical that are between 10 and 20 kilobytes.

![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/labreport3image12.jpg)

Example 3: ```` find ./*/* -size -10k | xargs grep --color=always -r 'fish'````

This finds the files smaller than 10 kilobytes and then finds which of their lines contains 'fish' and prints them. 

![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/labreport3image13.jpg)







<!-- ````
less -X <file>
````
This command keeps the opened file in the same terminal window as the main window. This helps if you want to keep seeing the contents of the file while typing other termninal commands. The benefit of this rather than cat is that it doesnt show the whole document at first and you press **enter** to show more. 
  
Example: ```` less -X  biomed/rr166.txt````

![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/labreport3image3.jpg)

````
less -N <file>
````

This commands shows the line number next to the text. 
  
Example: ````less -N  biomed/rr166.txt````

![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/labreport3image4.jpg)


## Command: Less -->