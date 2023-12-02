# Lab Report 4
## Vim Editor
---
### 4. Log into ieng6
![image](https://github.com/haley-gilmartin-chen/cse15l-lab-reports/assets/147003402/0c78330d-ef12-40b1-bf54-48745eccf418)
Keys Pressed: 
`<ssh cs15lfa23qd@ieng6.ucsd.edu><Enter>`
I used this command to enter my ieng6 account.


### 5. Clone your fork of the repository from your Github account (using the SSH URL)
![image](https://github.com/haley-gilmartin-chen/cse15l-lab-reports/assets/147003402/9db7d28e-6230-4af2-9fa6-0d675f200f0a)
Keys Pressed:
`<git clone git@github.com:haley-gilmartin-chen/lab7.git><Enter>`
I made a clone of my forked repository on my github account to my ieng6 computer.


### 6. Run the tests, demonstrating that they fail
![image](https://github.com/haley-gilmartin-chen/cse15l-lab-reports/assets/147003402/97425472-2dc5-4c93-b6ab-78e8f01eedef)
Keys Pressed:
`<ls><cd lab7><ls><bash test.sh>`
I first navigated into my cloned folder, `lab7`, and then ran `test.sh` using the `bash` command to test if my Junit test cases passed. They failed.


### 7. Edit the code file ListExamples.java to fix the failing test (as a reminder, the error in the code is just that index1 is used instead of index2 in the final loop in merge)
![image](https://github.com/haley-gilmartin-chen/cse15l-lab-reports/assets/147003402/8fcb9fa2-72af-403e-a906-53f11e67261c)

Keys Pressed:
`<vim ListExamples.java></index1/><enter><n>*9<l>*5<r><2><:wq>`
Using Vim editor, I opened `ListExamples.java` and then searched for `index1` instances using `/index1/`. I pressed `n` until I landed upon the correct instance, then navigated to the desired character by pressing `l`. After my cursor was over the `1` in `index1`, I pressed `r2` to replace it with a `2`, resulting in `index1` being changed to `index2`. I then saved and exited my file using `:wq`.

### 8. Run the tests, demonstrating that they now succeed
![image](https://github.com/haley-gilmartin-chen/cse15l-lab-reports/assets/147003402/f331bcdc-718b-4034-849d-5144bd54a12f)

Keys Pressed:
`<up>*2`
To check if the `ListExamples.java` edits were successful and if the Junit tests would now pass, I clicked the `<up>` arrow twice to navigate through my history and rerun `bash test.sh`.

### 9. Commit and push the resulting change to your Github account
![image](https://github.com/haley-gilmartin-chen/cse15l-lab-reports/assets/147003402/b8e765fa-72d1-44f7-9013-8c88c789f3ec)
![image](https://github.com/haley-gilmartin-chen/cse15l-lab-reports/assets/147003402/8afa2cd0-9dbe-4787-ae01-d1db6a2cee62)

Keys Pressed:
`<git push git@github.com:haley-gilmartin-chen/lab7.git><Enter>`
After my tests ran, I committed and pushed my changes to my repository. To verify the changes were made, I checked online and found that they had pushed.

