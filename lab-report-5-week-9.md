Dmitri Demler
  
A16992026
  
CSE 15L
# Lab Report 5

## Grading Student Submissions


Here is my **Grade.sh** code:

````
# used some ideas from this the repository https://github.com/kNelakonda/list-examples-grader/blob/main/grade.sh
FSCORE=0
MAXSCORE=100

function score_message() {
    printf "Student recieved $1/$2 \n"
    exit 0
}

rm -rf student-submission
git clone $1 student-submission
echo 'Finished cloning'

cp TestListExamples.java ./student-submission/

if [ -f ./student-submission/ListExamples.java ]; then
    echo found
    FSCORE=$((FSCORE + 10))
else
    echo not found java file
    score_message $FSCORE $MAXSCORE
fi

javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar student-submission/TestListExamples.java student-submission/ListExamples.java

if [[ $? -ne 0 ]]; then
    printf "Compiler did not work\n"
    score_message $FSCORE $MAXSCORE
fi

FSCORE=$((FSCORE + 20))

cd student-submission/

printf "_________running java now__________\n"

java -cp .:../lib/hamcrest-core-1.3.jar:../lib/junit-4.13.2.jar org.junit.runner.JUnitCore TestListExamples >output.txt

if [[ $? -eq 0 ]]; then
    cat output.txt
    FSCORE=$((FSCORE + 70))
else
    cat output.txt
    t=$(grep -i "Tests run" output.txt)
    tests=$(echo $t | cut -d ' ' -f 3 | cut -d ',' -f 1)
    failed=$(echo $t | cut -d ' ' -f 5)

    echo $((tests - failed))/$tests tests passed

    FSCORE=$((FSCORE + 35 * (tests - failed)))

fi

score_message $FSCORE $MAXSCORE

````


Here are some screenshots of running this on various example student submissions and the results that are shown.


For this [repository:](https://github.com/ucsd-cse15l-f22/list-methods-filename)

![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/labreport5image1.jpg)

-----

For this [repository:](https://github.com/ucsd-cse15l-f22/list-methods-corrected)

![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/labreport5image3.jpg)

----

For this [repository:](https://github.com/ucsd-cse15l-f22/list-methods-compile-error)

![Image](https://dimapdemler.github.io/cse15l-lab-reports/images/labreport5image2.jpg)


Trace of the most recent repository run (the one with the compile error).

- lines 1-4:
    
    ````
    FSCORE=0
    MAXSCORE=100
    ````
    Creates variables *MAXSCORE* and *FSCORE* which adds to itself as the program passes various tests.
- lines 5-8:
    ````
    function score_message() {
    printf "Student recieved $1/$2 \n"
    exit 0
    ````
    local function that outputs the final score in the end with the updated *FSCORE*. 
    the second line returns 0. The third ends the bash file early by returning 0.
- ````rm -rf student-submission````
    - Removes the old student submission folder. returns 0.
- ````git clone $1 student-submission````
    - git clones the repository indicated by the url (the input of the bash). Returns 0.

````
cp TestListExamples.java ./student-submission/

if [ -f ./student-submission/ListExamples.java ]; then
    echo found
    FSCORE=$((FSCORE + 10))
else
    echo not found java file
    score_message $FSCORE $MAXSCORE
fi
````
- cp copies the master TestListExamples java file into the student folder. returns 0. The if statement line is true for this repository since the student java file is named correctly. The echo command returns 0. Then the variable *FSCORE* is updated. The else statement is not run with this repository. 


- ````javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar student-submission/TestListExamples.java student-submission/ListExamples.java````
    - Runs the javac command on *junit*, *hamcrest core*, *TestListExamples*, and *ListExamples*. This returns 1 because it does not compile.  


- ````if [[ $? -ne 0 ]]; then````
    - This if statement is true because the javac returns an error (not 0) and thus the output is **not** 0. The compiler doesn't run because there is a missing semicolon.

- ````printf "Compiler did not work\n"````
    - prints a statement about the compiler not working. Returns 0. 

- ````score_message $FSCORE $MAXSCORE````
    - This runs the *score_message* function that I mentioned in the beginning. It returns 0. This then ends the bash run for this student submission. If the student had made a program that compiled, the bash would continue running.

