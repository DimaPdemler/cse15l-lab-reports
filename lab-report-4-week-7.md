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

![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/labreport4image4.jpg)

````dw <enter> i ````

This deletes the word start and then goes into insert mode

![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/labreport4image5.jpg)

```` base<esc>````

This inserts the text *base* to where *start* used to be

![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/labreport4image6.jpg)

```` :wq````

This quits the documents but also saves it.

![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/labreport4image7.jpg)

And this is how ou change *start* to *base* using vim!