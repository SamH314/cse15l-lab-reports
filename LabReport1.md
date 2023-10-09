# cd
1. an example of using the command with no argument


![Screenshot 2023-10-08 at 4 26 37 PM](https://github.com/SamH314/cse15l-lab-reports/assets/146782614/75bb0ff5-8c71-4124-a93a-975c1f0f20c6)

The working directory was home. I got that output because there was no change in directory since there was no argument. It stayed in the same directory. The output is not an error.

2. an exmaple of using the command with a path to a directory as an argument.

![Screenshot 2023-10-08 at 4 27 04 PM](https://github.com/SamH314/cse15l-lab-reports/assets/146782614/da5b3aec-1716-405d-bd3e-9ff6c617a816)

The working directory was home. Technically there was no output, but the directory did change. The directory changed from home to Lecture1. The output is not an error.

3. an example of using the command with a path to a file as an argument

![Screenshot 2023-10-08 at 4 30 38 PM](https://github.com/SamH314/cse15l-lab-reports/assets/146782614/276774cc-6a5b-4529-80cd-be6245a06c47)

The working directory was Lecture1. There was an error when changing directories to Hello.class. Hello.class is a file, not a directory. Therefore there was no directory to change to.

# ls
1. an example of using the command with no argument

![Screenshot 2023-10-08 at 4 36 09 PM](https://github.com/SamH314/cse15l-lab-reports/assets/146782614/977bcc49-d170-49af-b08e-2c93b3b57a7f)

The working directory was home. The output was the list of items inside home, which were lab1 and Lecture1. I got that output because LS is a command that list items inside a directory. The output is not an error.

2. an example of using the command with a path to a directory as an argument.

![Screenshot 2023-10-08 at 4 37 36 PM](https://github.com/SamH314/cse15l-lab-reports/assets/146782614/c52a15cd-b42a-4c5d-b4ca-b43c2a98829f)

The working directory was home. The output was the list of items that is inside lecture1, which are Hello.class, Hello.java, messages, and README. The output is not an error.

3. an example of using the command with a path to a file as an argument.

![Screenshot 2023-10-08 at 4 38 36 PM](https://github.com/SamH314/cse15l-lab-reports/assets/146782614/ded9c2b6-f67a-4c8b-9516-e928f5863528)

The working directory was home. The output was Hello.class because if you ls a file, it only lists that file. The output is not an error. 

# cat
1. an example of using the command with no argument

![Screenshot 2023-10-08 at 4 54 09 PM](https://github.com/SamH314/cse15l-lab-reports/assets/146782614/a07003f3-0649-463c-8e84-b493972d33ed)

The working directory was home. There was no output, cat is waiting for a keyboard input which will repeat any input and display it. The output is not an error because it was allowed.

2. an exmaple of using the command with a path to a directory as an argument.

![Screenshot 2023-10-08 at 4 54 46 PM](https://github.com/SamH314/cse15l-lab-reports/assets/146782614/51763071-21a3-420a-bf10-43b13e51866e)

The working directory was Lecture1. The output was an error. You can not cat a directory since its not a file that can be read. 

3. an example of using the command with a path to a file as an argument.

![Screenshot 2023-10-08 at 5 06 55 PM](https://github.com/SamH314/cse15l-lab-reports/assets/146782614/ec8c08a8-3139-418c-b5e8-c2e7fb874c57)

The working directory was messages. The output was Bonjour le monde! That's what was inside the text file fr.txt, which cat read and displayed for us. The output was not an error.

