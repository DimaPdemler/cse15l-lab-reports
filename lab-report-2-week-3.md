Dmitri Demler
  
A16992026
  
CSE 15L
# Lab Report 1

  
  
## Part 1:
Here is the code for the search engine method:

````
ArrayList<String> items2 = new ArrayList<String>();

    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    int num = 0;
    boolean fix1=true;
    public String handleRequest(URI url) {
        ArrayList<String> queryArray = new ArrayList<String>();
       
        if (url.getPath().contains("/add")) {
            String[] parameters = url.getQuery().split("=");
            if (parameters[0].equals("s")) {
                System.out.println(parameters[1]+ " -parameters");

                items2.add(parameters[1]);

                for(int i = 0; i < items2.size(); i++) {   
                    // System.out.print(items.get(i));
                } 

                
                // num += Integer.parseInt(parameters[1]);
                return String.format("Added keyword: "+ parameters[1]);
            }
            
        }
        else if (url.getPath().contains("/search")) {
            String[] parameters = url.getQuery().split("=");
            if (parameters[0].equals("s")) {
                for(int i = 0; i < items2.size(); i++) {   
                    if(items2.get(i).contains(parameters[1])){
                        if(fix1==true){
                            queryArray.add(items2.get(i));
                            fix1=false;
                        }
                        else{
                            fix1=true;
                        }
                        
                    }
                }
                return String.format("results: "+ queryArray);

            }
            
        }
        return "404 Not Found!";
````
*Note: I use the fix boolean variable because for some reason each method ran twice. I checked my own code and found no error. I believe that something is wrong with the source code. The fix1 variable helps negate this issue.*

Here are some screenshots of me implementing this code:

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

---

<br/>
<br/>

## Part 2:

The method reversed in the file ArrayExamples has a simple bug but it results in an output that is very different from the desired function. Most input arrays result in the wrong output. One such example is such:
````
@Test
  public void testreverse2() {
    int[] input1 = {1,2,3,4};
    // for(int elements : ArrayExamples.reversed(input1)){
    //   System.out.println(elements);
    // }
    assertArrayEquals(new int[]{4,3,2,1}, ArrayExamples.reversed(input1));
  }
````


This leads to a jUnit failure:
![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/cse15L_lab2_2pic5.jpg)

Basically, the array that is returned is a blank arrays of just zeros because the temporary array never copied the values of the original array. There are multiple ways to fix this code. I used a way that is a little less efficient but keeps the idea of the original code: 

````
 static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int j=0;j<arr.length;j+=1){
      newArray[j]=arr[j];
    }
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
````
I copied the contents of the original array onto the copied array and then the rest of the code could stay the same. If you check for any point of the the array it would return 0. This is why the junit test says that the first element returns 0 instead 4.
<br/>
<br/>
<br/>

---

The method filter in the file ListExamples almost does exactly what is being asked but flips it. Instead of returning value, say, [1,2,3] it returns [3,2,1]. One such example is this test method:

````
 @Test 
	public void testfilter() {
        List<String> list1 = new ArrayList<>();
        list1.add("fish");
        list1.add("meat");
        list1.add("juice");
        list1.add("cereal");
        list1.add("meat");

        String s1="fish";

        List<String> list2 = new ArrayList<>();
        list2.add("fish");
        list2.add("meat");
        list2.add("meat");
        // list2.add("juice");
        
        // ListExamples.StringChecker(s1)=true;
        assertEquals(list2, ListExamples.filter(list1, new StringChecker2()));

	}
````

with the checkString method being: 

````
public boolean checkString(String s){
    if(s.equals("meat")){
      return true;
    }
    else if(s.equals("fish")){
      return true;
    }
    return false;
  }
````

This returns the following result: 

![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/cse15L_lab2_2pic6.jpg)

This bug happens because it adds the final array to the beginning rather than the end. This means that the last elements will be first rather than at the end. As you can see from the inital output, the array is simply flipped and if you change the values it will stay being flipped. Here is the code that fixed this:

````
if(sc.checkString(s)) {
        result.add(s);
      }
````

By removing the index:0 from the code, this now works! 