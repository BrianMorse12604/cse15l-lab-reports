# Lab Report 4

In an attempt to improve efficiency when using commands on the command line, there are many shortcuts that can be used to do trivial jobs much faster. This report will display some of these tricks and explore how and why they are useful. We will explore the utility by accomplishing the following steps:
1. Log into ieng6
2. Clone your fork of the repository from your Github account
3. Run the tests, demonstrating that they fail
4. Edit the code file to fix the failing test
5. Run the tests, demonstrating that they now succeed
6. Commit and push the resulting change to your Github account (you can pick any commit message!)

---

## 1. Log into ieng6

![Log into ieng6]()

*Keys Pressed*: `<Ctrl+R>` s `<enter>`

The `ssh cs15lwi23afo@ieng6.ucsd.edu` command was in my local bash history so I used the shortcut Ctrl+R to search my past history. I then pressed "s" on my keyboard to search for past commands that contained the letter, which found the `ssh` command. I then pressed enter to run the command on the terminal.

---

## 2. Clone your fork of the repository from your Github account

![Clone git repo]()

*Keys Pressed*: git clone `<Ctrl+V><enter>`

Neither "git" nor "clone" can be autocompleted by any special shortcuts, but it was very important to use the Ctrl+V shortcut in order to paste the SSH GitHub repository link `git@github.com:BrianMorse12604/lab7.git` that was copied before any of the main process started. It is important to have the ssh version of the repository link so that no credentials will have to be put in for cloning or pushing. Enter was once again pressed to run the command.

---

## 3. Run the tests, demonstrating that they fail

![Run failing tests]()

*Keys Pressed*: cd l `<tab><enter>`, `<Ctrl+R>` javac `<enter>`, `<Ctrl+R>` T `<enter>`

In order to guarentee that the java commands will run as intended, I first had to enter the directory that I cloned from GitHub. "cd" had to be manually typed but the directory could be autocompleted from "l" to "lab7/" by pressing `<tab>` since there was only one path in the directory that started with "l". Once in the directory, I knew that both my `javac` and `java` commands were stored somewhere in my history, so I used Ctrl+R like in step 1 to search past commands. For the command `javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java` I searched for "javac" since just using "java" would apply to too many commands but the extra "c" differentiated the command from the rest. Then for the command `java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests` I searched for "T" since the java command was the only recent command to use that character. Enter was used to run each of these commands.

## 4. Edit the code file to fix the failing test

![Edit the code file]()

*Keys Pressed*: `<Ctrl+R>` sed `<enter>`

The command `sed -i '43 s/index1/index2/' ListExamples.java` is a command that has not been covered by the course so far but was useful in editing the file without using a text editor such as Vim or Nano and then having to search within the file to fix the bug. The `-i` option means that the command would edit and save the file within itself instead of printing the results in standard output. The term `'43 s/index1/index2/'` is what is used to actually fix the bug. The line means to go to line 43 in the designated file and substitute the first instance of "index1" with "index2". The final argument of "ListExamples.java" just means to run the command on that file. This command was in my bash history so using Ctrl+R and searching "sed" was necessary to narrow down the search to the exact command. Enter was used to run the command.

---

## 5. Run the tests, demonstrating that they now succeed

![Run passing tests]()

*Keys Pressed*: `<up><up><up><enter>`, `<up><up><up><enter>`

Because the commands we need to run for step 5 are the exact same commands from step 3, I can use the up arrow to traverse my most recently ran commands to find them once again. Since I know exactly which commands have been run so far, I know that my full `javac` command is three commands up, hence why the up arrow is pressed three times. After the `javac` command, my full `java` command used to be two commands up but is now three commands up, so the up arrow has to be pressed three times once again. Enter is pressed to run each command.

---

## 6. Commit and push the resulting change to your Github account

![Commit and Push]()

*Keys Pressed*: git add L `<tab>` .j `<tab><enter>`, git commit -m 's' `<enter>`, git push `<tab>` m `<tab><enter>`

Much of the `git` commands can not be autocompleted, but there are still some shortcuts to save a little time and prevent typos. For the first command, when trying to put in the file to add, I start with just "L" before hitting tab to autocomplete to "ListExamples". It does not immediately fully autocomplete because there are multiple paths that meet that term. Due to that, I type ".j" and hit tab to complete to "ListExamples.java" which is the full file name wanted. For the commit there is no autocompletion possible, but the commit message was made only one letter to be quicker (even if not descriptive). For the final command, after "git push " is typed, hitting tab will autocomplete "origin" and then typing "m" and tab will autocomplete to "main", finishing the command. Enter was pressed to run all of the commands.

---

As can be seen from all of the steps, there are many ways to save time when writing commands in a bash terminal. Not only will the shortcuts save you some time of not having to type it all out every time, it will also help to prevent any possible typos the user may cause. This limits bugs and makes the overall life of the programmer better, so knowing and mastering these tools will only be beneficial for future work.
