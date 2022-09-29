Dmitri Demler
  
A16992026
  
CSE 15L
# Lab Report 1

Connecting to a different server can seem like a daunting task but fear not! This document will help guide you to connect to one such server and make life easier as well.

1. •	Step 1: installing VScode
    -	VScode is a popular programming application due to its flexibility with many different languages
    -	To install it, go to [link](https://code.visualstudio.com/download) and go to your operating system. Follow their steps for installation. When you first download it, you are given various extensions to download depending on your needs. I recommend downloading the python and Java extensions if you desire to use those languages.
2. •	Step 2: Remotely Connecting
    - To remotely connect to a server, you need to have a cse 15L account. You need to set your password for the course-made accounts. To do this, go to [link](https://sdacs.ucsd.edu/~icc/index.php) go to your account and choose the option to reset global account. 
    - Reset your account and make sure that your select the “Change course-specific account passwords” and wait up to 15 minutes for the changes of password to go through. Personally, this was the hardest step because I mistyped my password at first and had to reset it again before the next steps worked. 
    - To remotely connect, find your two letter code that you find in your account information on the previously mentioned url link. Open terminal on you computer and put this code: 
    ````ssh cs15lfa22zz@ieng6.ucsd.edu````
    but instead of “zz” put in your two letter code. If it is your first time connecting it will ask to continue connecting and type “yes”
    - Following that it will ask for your password and you type it in the box. Press “enter” after you are done typing. This is what you should see after you log in: 
    - ![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/cse15L_lab1_image1.jpg)
    - You are now connected to the remote server!
3. Step 3: Trying some commands
    -Now try some commands on both your personal device and the connected server. Some commands worth trying are 
    ````
    cd ~
    cd
    ls -lat
    ls -a
    cp /home/linux/ieng6/cs15lfa22/public/hello.txt ~/
    cat /home/linux/ieng6/cs15lfa22/public/hello.txt
    ````
    - “ls ~” from personal device: ![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/cse15L_lab1_image2.png)
    - “ls ~” from server: ![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/cse15L_lab1_image3.png) Note: you will not have “WhereAmI.java” until the next few steps.
    - o	To exit from the server type ````exit````
4. Step 4: Moving Files with scp
    - To move files between your connected server and personal device, you need to create a file to move. Make a java file called “WhereAmI.java” which contains: 
     
    ````
    class WhereAmI {
    public static void main(String[] args) {
        System.out.println(System.getProperty("os.name"));
        System.out.println(System.getProperty("user.name"));
        System.out.println(System.getProperty("user.home"));
        System.out.println(System.getProperty("user.dir"));
    }
    }
    `````
    - Try running this file on your personal device. I had an issue of not having java downloaded so I went to [link](https://www.oracle.com/java/technologies/downloads/#jdk19-mac) and downloaded it. 
    - Following that in terminal in the directory of where this file is stored type “javac WhereAmI.java” and then “java WhereAmI”. This should run the python file ![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/cse15L_lab1_image4.jpg)
    - To transfer this file to the server, type 
    ```` scp WhereAmI.java cs15lfa22zz@ieng6.ucsd.edu:~/```` 
    You will then be asked for the password and type that. 
    - You should see a similar terminal screen:
    ![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/cse15L_lab1_image5.jpg)
    - Running the previous commands of the java file on this server should give u these results:
    ![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/cse15L_lab1_image6.jpg)
5. Step 5: Setting up an SSH key
    - Because you need to type your password each time you need to access the server, it can waste a lot of your time. To login automatically you need to create an SSH key on your device.
    - On you personal device type “ssh-keygen”, then choose where you want to store it. It will then ask for a passphrase and you can type one or leave it blank by pressing enter. 
    - ![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/cse15L_lab1_image7.jpg)
    - o	If you are using windows you will need to follow the extra steps using this [link](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_keymanagement#user-key-generation). 
    - On the personal terminal type 
    ```` 
    ssh cs15lfa22zz@ieng6.ucsd.edu
    ```` 
    with the different letter combination as before. Then type your password.
    - One the server terminal, type “mkdir .ssh”  and return back to the personal server.
    - Finally, type 
    ````
    scp /Users/dimademler/.ssh/id_rsa.pub cs15lfa22zz@ieng6.ucsd.edu:~/.ssh/authorized_keys
    ````
    - The next time you try to enter the server, you will no longer need to type your password!  

    - ![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/cse15L_lab1_image8.jpg)
6. Step 6: Optimizing remote Running
    - You can optimize the process of updating a file you edit locally by combining several commands.
    - The fastest way I found to do this is to edit the code on VScode and then type the following code: 
    ````
    cd /Users/dimademler/Downloads/; scp WhereAmI.java cs15lfa22er@ieng6.ucsd.edu:~/; ssh cs15lfa22er@ieng6.ucsd.edu
    ````
    - o	Then type 
    ````
    javac WhereAmI.java; java WhereAmI; exit” 
    ````
    - This is the fastest way I found to edit, move, and run the java file on the server. 





