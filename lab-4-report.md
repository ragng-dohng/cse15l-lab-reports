Reproduce the task from the competition on your own
For steps 4-9: screenshot & write exactly which keys you pressed to get to that step.
*special characters like <enter> or <tab>, write them in angle brackets with code formatting. 
Then, summarize the commands you ran and what the effect of those keypresses were.

#### 4. Log into ieng6
- copy and paste the default `ssh cs15lwi23zz@ieng6.ucsd.edu`
- change into my specific account: `ssh cs15lwi23ajm@ieng6.ucsd.edu`
  - 15x `<left-arrow>` (until cursor highlights at @)
  - 2x `<back-space>` to delete the default `zz`
  - type my specific code `ajm`
  - `<enter>` which automatically ssh into the remote ieng6 account without a password (prior setup)

![image](https://user-images.githubusercontent.com/111631103/224881312-ff7083f3-55c5-41a6-8669-cef22b9b9216.png)
  
#### 5. Clone your fork of the repository from your Github account
- get the ssh-key from the relevant repository
  
![image](https://user-images.githubusercontent.com/111631103/224881846-f6ed4bf6-98d2-41fb-b9ad-9a03bf852a1d.png)
  
- `git clone git@github.com:rang-dohng/lab7.git` (note the ssh-key was copied and pasted into the command
  
![image](https://user-images.githubusercontent.com/111631103/224883711-52d3a68b-3040-4668-ae17-9e6172a88196.png)
  
- remember to `cd ~/lab7` in order to operate within it

#### 6. Run the tests, demonstrating that they fail
- we need to compile all the java files before running the test: `javac -cp ".:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar" *.java`
- now, we run the test with `java -cp ".:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar" org.junit.runner.JUnitCore TestListExamples`
*note, that the remote account uses Unix/Linux, so the commands above are likeso.

![image](https://user-images.githubusercontent.com/111631103/224884648-b7a50e33-c293-4c06-8457-32c5b6c9df9c.png)

#### 7. Edit the code file to fix the failing test

