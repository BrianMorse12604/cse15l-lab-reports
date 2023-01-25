# Lab Report 1
This is a tutorial on how to get **remote access** to a server on your client computer and explore some basic commands that will be useful for 
future work in computer science. It includes downloading some crucial software such as Visual Studio Code and Git Bash to a demonstration of connecting
to a remote server and using commands to navigate the space

---

## Step 1 - Installing VS Code
* If you have already set up VS Code (Visual Studio Code) like I had, then you may skip the rest of this step. However if you have not, continue reading
* Go to the following link [VS Code](https://code.visualstudio.com/) and click download in the upper right corner to see the following page

![VS Code Download Page](Screenshot%20(8).png)

* Make sure to choose the right download for your device and follow all instructions provided on the page until you can open up the software and see a page like so

![VS Code Blank Page](Screenshot%20(6).png)

---

## Step 2 - Remotely Connecting
* If you do not have git installed on your device, download git [here](https://gitforwindows.org/) so that you can use `git bash`
* Next open up a bash terminal by doing Ctl + \` or going to Terminal and clicking new Terminal on VS Code and use the following command utilizing `ssh`, but replace the server address with the server address that you are assigned and have access to
```
$ ssh cs15lwi23afo@ieng6.ucsd.edu
```
* If it is your first time connecting to this server, you will be prompted if you want to continue, type *yes*. It will then ask for your password. Put in the complete password you have associated with the account, the terminal will not show that you are typing anything, but it is still tracking the results. Once the password is fully typed in, press enter
* If all went well, you should now be connected to the remote server and have access to the information there as displayed

![Entered Remote Server](Screenshot%20(7).png)

>**NOTE** If this is your first time entering the server, you will have more opening text than what is displayed here, but as long as this is similar to the end of the output provided, you have successfully gotten connection

---

## Step 3 - Run Some Commands
* Now that you are connected to the remote server, test out some commands such as changed directory: `cd`, list: `ls`, or looking at the text of files: `cat`
* Test out these commands on both the remote server and your client computer as they will have different results due to containing different files and folders, which can be seen and displayed via these tests, like in the image below
* By running these commands, I learned it is quite possible to change the output delivered based on what additional information you give the command. For example, by adding different options after the `ls` command, such as `-lat`, we drastically change how the information is sorted and displayed. By doing `-l`, we got all of the access information for the files, `-a` displayed the hidden files, and `-t` sorted the files by the time it was last edited, which creates a different and interesting output compared to the standard version of the command

![Tested Commands](Screenshot%20(5).png)

* Once you are done testing commands, use Ctl-D or the command `exit` to disconnect from the remote server

---

**Congrats!** You now should be able to connect to a remote server and manipulate the connection to do different jobs, this will be a very important thing to know for future parts of CSE 15L
