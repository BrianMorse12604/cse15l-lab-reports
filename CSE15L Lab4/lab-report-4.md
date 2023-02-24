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
