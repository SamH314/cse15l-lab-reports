# Part 1 - Debugging Scenario

## Student EdStem Post:

![Screenshot 2023-12-02 at 1 58 06 PM](https://github.com/SamH314/cse15l-lab-reports/assets/146782614/c3037d79-7642-42e6-b50a-4ee8477082bf)

"I seem to be having trouble with `LIST-EXAMPLES-GRADER`. My files seem to be cloning and are being found, but they are not compiling or being tested. I'm not sure what I'm doing wrong."

## TA Response:

"Hi, Sammy. Thanks for reaching out. I see what your problem is and I will try my best to guide you without giving too much away to encourage a learning opportunity. I would suggest to keep in mind what your current directory is. The command, `echo "This is my current directory $PWD"` after `cd grading-area` should give you an idea. The terminal seems to indicate that the JAR files `hamcrest-core-1.3.jar` and `junit-4.13.2.jar` (located in the `/lib` directory) aren't being found in the directory you currently are in. Hint: Is there a way to edit the paths for `java` and `javac` to `cd` into the `lib` directory?"

## Student Response to TA:
![Screenshot 2023-12-02 at 2 46 20 PM](https://github.com/SamH314/cse15l-lab-reports/assets/146782614/20f2f079-5df2-4c62-8733-3f020bfe8151)

"Thank you for the help. Running the command `echo "This is my current directory $PWD"` made me see that I was in `grading-area` directory and not in `lib` where the JAR files are located. This is why I was getting not found errors when running the commands. I fixed this by adding  `..` before every `/lib` pattern in my   `java` and `javac` commands in order to fix the path by going back a directory. With this fix I was able to `cd` into the `lib` directory and run the `java` and `javac` commands"

## Information Needed About the Setup:
### The File & Directory Structure Needed:

![Screenshot 2023-12-02 at 3 35 17 PM](https://github.com/SamH314/cse15l-lab-reports/assets/146782614/7ac80ee5-efdd-464c-85de-db47df7fcaab)

### The Contents of Each File Before Fixing the Bug:
```
CPATH='.:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar'

rm -rf student-submission
rm -rf grading-area

mkdir grading-area

git clone $1 student-submission
echo 'Finished cloning'

student_submission="student-submission/ListExamples.java"
destination_directory="grading-area/"


if [[ -f $student_submission ]]
then
    echo "File found"
    cp -r "$student_submission" "$destination_directory"
    cp -r TestListExamples.java "$destination_directory"
else 
    echo "File not found"
    exit 1

fi

set +e


# javac grading-area/ListExamples.java
cd grading-area

javac -cp .:/lib/hamcrest-core-1.3.jar:/lib/junit-4.13.2.jar *.java

java -cp .:/lib/hamcrest-core-1.3.jar:/lib/junit-4.13.2.jar org.junit.runner.JUnitCore TestListExamples

if [ $? -ne 0 ]; then
  echo "compiling failed"
  exit 1

fi
```
### The Full Command Line (or Lines) You Ran to trigger the Bug:
`bash grade.sh https://github.com/ucsd-cse15l-f22/list-methods-corrected`
### A description of What to Edit to Fix the Bug:
`javac -cp .:../lib/hamcrest-core-1.3.jar:../lib/junit-4.13.2.jar *.java`
`java -cp .:../lib/hamcrest-core-1.3.jar:../lib/junit-4.13.2.jar org.junit.runner.JUnitCore TestListExamples`
adding `..` before every `/lib` pattern in the `java` and `javac` commands

# Part 2 - Reflection

Honestly, how extensive the git commands are. The steps that are needed to to reflect the changes of your code on github. Such as `git add`, `git commit`, and `git push`. I also enjoyed learning about vim, how I can start coding from the terminal if I wanted to. It's also very interesting learning all the vim shortcuts and how it effective/faster they are supposed to be. It's very interesting the solutions they went around for removing the use of a mouse, such as having differnet modes like insert and visual. I also found it interesting that we could write the java versions of bash scripts as well.  
