# Lab Report 4 - SSH keys, Cloning into a remote account, Using nano (a command-line text-editor), and Saving changes to Github

_Behind-the-Scenes_: 
SSH keys was setup for both ieng6 (a remote course-specific server) and GitHub to access/write data in repositories on GitHub.com to avoid having to repeatably enter passwords. The process involves:
1. generate an SSH key on ieng6
2. copy it to an ieng6 account
3. add the public key to an Github account

Generally, SSH keys makes it easier and quicker to access remote accounts and repositories without having to worry about password authentication, e.g. the ieng6 server and GitHub. 

The following is the latter steps (steps 4-9) in which we tested the connection by cloning the repository, fixed the code to pass the test, and commit and push the changes to Github.

### 4. Log into ieng6
- copy and paste the default `ssh cs15lwi23zz@ieng6.ucsd.edu`
- change into my specific account: `ssh cs15lwi23ajm@ieng6.ucsd.edu`
  - 15x `<left-arrow>` (until cursor highlights at @)
  - 2x `<Backspace>` to delete the default `zz`
  - type my specific code `ajm`
  - `<Enter>` which automatically ssh into the remote ieng6 account without a password (prior setup)

![image](https://user-images.githubusercontent.com/111631103/224881312-ff7083f3-55c5-41a6-8669-cef22b9b9216.png)
  
### 5. Clone your fork of the repository from your Github account
- get the ssh-key from the relevant repository
  
![image](https://user-images.githubusercontent.com/111631103/224881846-f6ed4bf6-98d2-41fb-b9ad-9a03bf852a1d.png)
  
- `git clone git@github.com:rang-dohng/lab7.git` (note the ssh-key was copied and pasted into the command
  
![image](https://user-images.githubusercontent.com/111631103/224883711-52d3a68b-3040-4668-ae17-9e6172a88196.png)
  
- remember to `cd ~/lab7` in order to operate within it

### 6. Run the tests, demonstrating that they fail
- we need to compile all the java files before running the test: `javac -cp ".:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar" *.java`
- now, we run the test with `java -cp ".:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar" org.junit.runner.JUnitCore TestListExamples`
*note, that the remote account uses Unix/Linux, so the commands above are likeso.

![image](https://user-images.githubusercontent.com/111631103/224884648-b7a50e33-c293-4c06-8457-32c5b6c9df9c.png)

### 7. Edit the code file to fix the failing test
- pull up the relevant code in nano (a command-line text-editor): `nano ListExamples.java`
  - use `<n><a><n><o> <L><Tab><j><a><v><a>` to autofill the rest of the file name
- navigate through code using arrows
- save changes with `<Ctrl>` + `<O>` and press `<Enter>`
- exit nano with `<Ctrl>` + `<X>`

![image](https://user-images.githubusercontent.com/111631103/224888237-6a5c7b6e-0fa6-4046-bc73-34beb3f7b33e.png)

### 8. Run the tests, demonstrating that they now succeed
- compile the code again
  - `<up-arrow>` until you see the former javac command `javac -cp ".:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar" *.java` then `<Enter>`
- run the test again
  - `<up-arrow>` until you see the former java command `java -cp ".:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar" org.junit.runner.JUnitCore TestListExamples`

![image](https://user-images.githubusercontent.com/111631103/224888887-25ceac90-3a94-43e6-ab69-998e613c9ef1.png)


### 9. Commit and push the resulting change to your Github account (you can pick any commit message!)
- `git add ListExamples.java` (again, we can use `<Tab>` to autofill the rest of the filename
- `git commit -m "fix code"`
- `git push`

![image](https://user-images.githubusercontent.com/111631103/224889503-0b62973a-1219-4a13-a34e-681d1599cf32.png)

### Quick Thoughts
Overall, the specific tasks were made more efficient with the use of `<Tab>` to autofill for the filenames which also decreases chances of mistypo. Also, navigating with the `<up-arrow>` and/or `<down-arrow>` to go through previously executed commands expediated the process. I also used `<Ctrl>` + `<C>` to discontinue my mis-typed commands running. And of course copy-and-paste was quintessential. 
