Dmitri Demler
  
A16992026
  
CSE 15L
# Lab Report 1


![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/cse15L_lab2_pic1.jpg)

- when this url is run, the method handleRequest runs. since the url root contains "add" the according if statement runs. The value after the s which is "mreat" is then added to the array.
- If this was the first add run on the local website, then the array will simply contain "mreat". This is because parameters[1] is "mreat".
- if this was not the first add, parameters would change to match the url inputted by the user. items2 the array that stores all the data is increased by the value inputted.


![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/cse15L_lab2_pic2.jpg)

- When this url is run, the method handleRequest runs. Since the url contains "search", it runs the corresponding if statement. This method looks for all elements that contain the string "eat". It then returns all these values. 
- we create a queryArray array that is empty at first. There also is a fix1 boolean variable that is initially true. items2 is the array that contains all the added elements. Its value is [create ,meat, feet, food, create, door, seat, create, meat, mreat] This does not change when the link is run.
- At the end, queryArray contains only the elements of the original array that contain the searched string. queryArray iterates through every element of the original array. The program then returns this queryArray. the fix1 variable changes back and forth between true and false during the for loop. 
  
  
![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/cse15L_lab2_pic3.jpg)

- When this url is run, the method handleRequest runs. Since the url contains "search", it runs the corresponding if statement. This method looks for all elements that contain the string "nothinghere". It then returns all these values. 
- as the previous screenshot, we create a queryArray array that is empty at first. There also is a fix1 boolean variable that is initially true. items2 is the array that contains all the added elements. its value is [create ,meat, feet, food, create, door, seat, create, meat, mreat] This does not change when the link is run.
- For this case, queryarray does not change because there are no strings that contain "nothinghere". This means it stays null. 
