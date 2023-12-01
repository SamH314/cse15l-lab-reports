# Step 4

<img width="520" alt="Screenshot 2023-11-16 at 1 23 58 PM" src="https://github.com/SamH314/cse15l-lab-reports/assets/146782614/0aa8084b-03c2-4d7e-a2f9-d84a8d6d265b">

`<up> <up> <enter> ` 

I clicked the up arrow two times to access my previous commands and pressed enter as soon as I saw `ssh cs15lfa23ek@ieng6.ucsd.edu`, as to login into a remote server in the CSE computer lab.

# Step 5

<img width="524" alt="Screenshot 2023-11-16 at 1 32 46 PM" src="https://github.com/SamH314/cse15l-lab-reports/assets/146782614/7129abd3-8d8e-41d9-8336-3275b07221a6">

I typed the commmand `git clone git@github.com:SamH314/lab7.git <enter>` to clone the fork of my repository from my github account using the ssh url.

# Step 6

<img width="870" alt="Screenshot 2023-11-16 at 1 46 26 PM" src="https://github.com/SamH314/cse15l-lab-reports/assets/146782614/e7932f42-66ae-4a59-9640-f4b679930e40">

I typed the command `cd lab7 <enter>` to change my current directory to lab7. Then I typed the command `ls lab7 <enter>` in order to see the contents of the current directory. Then I typed  `bash test.sh <enter>` in order to run the bash script that compiles and runs  `ListExamples.java ListExamplesTests.java` which ran the test that demonstrated the errors.
# Step 7

<img width="397" alt="Screenshot 2023-11-16 at 1 51 06 PM" src="https://github.com/SamH314/cse15l-lab-reports/assets/146782614/3800e9b6-930d-4523-a8f1-df8b02ecd530">

I typed the command `vim ListExamples.java <enter>` in order to edit `ListExamples.java` file. I then typed `<shift> ; 44` to go to line 44 where the error seems to be. I clicked `l` 6 times in order to get to the index number I need to change, to make index1 become index2. I clicked `i` to get into insert mode and hit `<delete> 2 <escape>` to make the change and escape out of insert mode. 

<img width="846" alt="Screenshot 2023-12-01 at 12 14 00 PM" src="https://github.com/SamH314/cse15l-lab-reports/assets/146782614/6ef80edb-7be6-45dd-a435-23434ca01290">

To save the change and quit out of vim I typed the command  `:wq <enter>`
# Step 8

<img width="505" alt="Screenshot 2023-11-16 at 5 42 12 PM" src="https://github.com/SamH314/cse15l-lab-reports/assets/146782614/42667e5b-c1d9-4602-96c8-eddd8a7c7c8c">

Being back in the terminal, I ran `bash test.sh` in order to run the test and show that they succeed.

# Step 9
<img width="778" alt="Screenshot 2023-11-16 at 5 58 17 PM" src="https://github.com/SamH314/cse15l-lab-reports/assets/146782614/1ad70312-b216-48ea-85b7-5e871c911ef0">

I checked the status of the directory by running the command `git status <enter>` which showed me what files were modified, in this case it was `ListExamples.java`. I ran the command `git add ListExamples.java <enter>` which prepared the file to be commited by git. Once more I typed `git status <enter>` to verify that my changes are staged to be committed. I finaly typed `git commit <enter>` to commit and push the changes into my github account. 

<img width="771" alt="Screenshot 2023-11-16 at 5 55 12 PM" src="https://github.com/SamH314/cse15l-lab-reports/assets/146782614/1631ee43-20da-40de-9de7-3a91c6d58208">

I went into insert mode `i <enter>` and added the commit comment `This change was made for my LabReport7. :) <escape>` I clicked the escape button to exit insert mode. I saved and quit by typing `<shift>;wq <enter>`.

![Screenshot 2023-11-19 at 5 52 49 PM](https://github.com/SamH314/cse15l-lab-reports/assets/146782614/e79b2616-2802-46bb-add3-d6fc2664b044)

I then typed git push `git push -u origin main <enter>` to push the changes onto my github.


The picture show's the changes are reflected onto my github.
![Screenshot 2023-11-19 at 5 54 15 PM](https://github.com/SamH314/cse15l-lab-reports/assets/146782614/05eb2af8-aa85-4f8d-93fc-e7cd0d321e10)
