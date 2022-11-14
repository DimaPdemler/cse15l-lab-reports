Dmitri Demler
  
A16992026
  
CSE 15L
# Lab Report 3

## Part 1: Changing the name of the **start** parameter to **base**

````/start <enter>````

*/start* moved the cursor to the first occurance of the string start
![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/labreport4image1.jpg)

````dw````

This deletes the word that the cursor is on in this case it is *start*

![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/labreport4image2.jpg)

````i<enter>base<esc>````

This adds the text *base* to the cursor location

![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/labreport4image3.jpg)


````n````

This finds the next instance of *start*

![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/labreport4image4.jpg)


````dw <enter> i ````

This deletes the word start and then goes into insert mode

![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/labreport4image5.jpg)

```` base<esc>````

This inserts the text *base* to where *start* used to be

![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/labreport4image6.jpg)

````n````

This finds the next instance of *start*

![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/labreport4image8.jpg)

````dw <enter> i ````

This deletes the word start and then goes into insert mode

![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/labreport4image9.jpg)

```` base<esc>````

This inserts the text *base* to where *start* used to be

![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/labreport4image10.jpg)

```` :wq````

This quits the documents but also saves it.

![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/labreport4image7.jpg)

And this is how to change *start* to *base* using vim!



## Part 2: Using local editors vs. vim

vim is very useful when trying to edit a file inside a remote server. However, the question of whether it's faster to run programs locally and copying them to the remote server vs. using vim is a hard one. 

After doing a few practice runs, I was able to make the edits shown above in around 45 seconds. The execution was not nearly perfect and I am sure I could cut it to around 20 seconds if I try for an hour or so. 

When I used vscode locally and scp'd it to the remote server it took about a minute and 10 seconds. However, this included first git cloning remotely and cp'ing the files locally, editing them, and then scp'ing them back remotely. As I learned the first time, copying a huge folder like *technical* is very slow, it was running for about 5 minutes before I stopped it. In the end, I decided to copy only the necessary files and this took much less time. 

The method I prefer to use depends on the situation. When I am writing complex code for a long time I prefer to use vscode because it has a lot of useful features like fill-in-the-blank and shortcuts that can save countless minutes. However, when I need to change a small detail in the code, I would prefer to use vim in the remote server. I believe that if the task at hand takes more than a few lines of code to change, then running it locally in vscode is better. But as you can see, in the situation of small edits, running it on vim is better.

