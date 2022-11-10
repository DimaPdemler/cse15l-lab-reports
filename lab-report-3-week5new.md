Dmitri Demler
  
A16992026
  
CSE 15L
# Lab Report 3

## Command: Less

By itself the command **less** opens a user defined file in a seperate terminal window helping keeping the original terminal window clean and organized. You can leave the window by pressing Q.

````
less -p[pattern] <file>
````

This command opens the file as before but highlights the pattern you typed in the command. This is helpful if you are looking for a spciefic word in a document. The patterns can be various useful keywords that can be adapted to your specific needs. 

**Example 1:**

````less -pcell biomed/rr166.txt````

![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/labreport3image2.jpg)

**Example 2:**

```` less -pantigen biomed/rr171.txt ````

![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/3pic1.jpg)

**Example 3:**

````less -pre biomed/rr171.txt````

![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/3pic2.jpg)



----

````
less -X <file>
````

This command keeps the text in the same terminal window as you run it. This means that you will be able to see the document even after you close the less window like normal. This helps if you want to see the contents of the file you opened while using the terminal.

**Example 1:**

````less -X biomed/rr171.txt````

![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/3pic3.jpg)

As you can see, you still have the text in the normal terminal screen

**Example 2:**

```` less -X biomed/rr196.txt ````

![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/3pic4.jpg)

You still scroll like you normally do, so the text will not clutter your screen like commands like **cat** would. You can choose which screen to keep in the the terminal window.

**Example 3:**

````less -X plos/pmed.0020210.txt````

![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/3pic5.jpg)

----

````
less -m <file>
````

This command lets you see your progess of reading the file. This helps if you are reading a long file and want to know how much more you need to read.

**Example 1:**

````less -m plos/pmed.0020210.txt````

![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/3pic6.jpg)

You can see the progress percent on the bottom left corner.

**Example 2:**

```` less -m biomed/rr196.txt ````

![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/3pic7.jpg)



**Example 3:**

````less -m biomed/rr171.txt````

![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/3pic8.jpg)

