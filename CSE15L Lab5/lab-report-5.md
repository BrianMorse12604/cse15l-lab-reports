# Lab Report 5

Being able to know how to use commands on the command-line efficiently is extremely useful to expand what is possible in finding data in a shorter period of time. So by looking into the many options of `find` we can figure out how to investigate into files within a directory and get information from all of the subdirectories and files within that directory. It is for this reason that I will be looking into four interesting options in `find` to be able to solve different problems.

---

## Name Searching: `find -name`

Sometimes, instead of just doing a general search for everything in a directory, you could just be looking for files with a very particular name or extension. This can be accomplished by using the `-name` option. By providing a name to the command, the `find` command will only return the files it finds that meets the name requirement, which is useful for really narrowing down on what you need.

```
$ find written_2/ -name "Beijing-History.txt"
written_2/travel_guides/berlitz2/Beijing-History.txt
```

* By providing a very specific file name, `find` was able to get the exact location of where that file called "Beijing-History.txt" is stored within the directory as a whole
* This utility can be very helpful if you know what you are looking for but have it lost within a given directory, this is a very fast way to locate how to access the file once again

```
find written_2/non-fiction/OUP/Kauffman/ -name "*.txt"
written_2/non-fiction/OUP/Kauffman/ch1.txt
written_2/non-fiction/OUP/Kauffman/ch10.txt
written_2/non-fiction/OUP/Kauffman/ch3.txt
written_2/non-fiction/OUP/Kauffman/ch4.txt
written_2/non-fiction/OUP/Kauffman/ch5.txt
written_2/non-fiction/OUP/Kauffman/ch6.txt
written_2/non-fiction/OUP/Kauffman/ch7.txt
written_2/non-fiction/OUP/Kauffman/ch8.txt
written_2/non-fiction/OUP/Kauffman/ch9.txt
```

* In this example, a "\*" was utilized to allow a more general name search within the directory "written_2/non-fiction/OUP/Kauffman". The wildcard tied with the `-name` option allows for the search of all .txt files instead of one with a particular name
* This is useful as it allows you to get all the files of a certain extension type, differentiating and separating said files from other extensions and files that may also exist within the same directory

For more examples and where this info was found, go here: [https://linuxhandbook.com/find-command-examples/](https://linuxhandbook.com/find-command-examples/)

---

## File type: `find -type`

Sometimes when you are looking through a directory, you do not want all the directories, files, and other aspects of the file structure all together. The `-type` option allows for you to specify what you are looking for, whether you just want the actual files within the directory or just the subdirectories. This can help declutter the searching field and allows for a better specificity so that the user knows they are only getting the type of file that may work for another command or analysis.

```
$ find written_2/ -type d
written_2/
written_2/non-fiction
written_2/non-fiction/OUP
written_2/non-fiction/OUP/Abernathy
written_2/non-fiction/OUP/Berk
written_2/non-fiction/OUP/Castro
written_2/non-fiction/OUP/Fletcher
written_2/non-fiction/OUP/Kauffman
written_2/non-fiction/OUP/Rybczynski
written_2/travel_guides
written_2/travel_guides/berlitz1
written_2/travel_guides/berlitz2
```

* This example looks for all the directory folders within the "written_2" directory. This is done due to the type "d" placed after `-type`, standing for directory.
* Finding all of the subdirectories can be quite useful as it can be used to find the overall structure of the files as to where everything is without having all of the clutter of the files within the directories.

```
$ find written_2/non-fiction/OUP/Fletcher/ -type f
written_2/non-fiction/OUP/Fletcher/ch1.txt
written_2/non-fiction/OUP/Fletcher/ch10.txt
written_2/non-fiction/OUP/Fletcher/ch2.txt
written_2/non-fiction/OUP/Fletcher/ch5.txt
written_2/non-fiction/OUP/Fletcher/ch6.txt
written_2/non-fiction/OUP/Fletcher/ch9.txt
```

* This example provides only the files that can be found in the "written_2/non-fiction/OUP/Fletcher/" directory. This is done due to the "f" standing for file provided to `-type`
* Having the `find` command only send back the files can be useful in case a command is being run that can only take files as input and you do not want the directories to be spoiling the batch of data to analyze. 
* Even if the directory you give the command only has files in it, this way it is not printed itself along with all of the other files.

For more examples and where this info was found, go here: [https://linuxhandbook.com/find-command-examples/](https://linuxhandbook.com/find-command-examples/)

---

## Finding Big or Small Files: `find -size`

Sometimes, when you are looking through your files, you may want to filter some out based on how large or small of the file may be in terms of storage space. This could be used when trying to declutter and making space on your PC or just trying to figure out where data is being stored. That is when the `-size` command option comes in. You can search for files larger than, smaller than, or equal to a certain size of data.

```
$ find written_2/ -size +250k
written_2/travel_guides/berlitz1/WhereToFrance.txt
written_2/travel_guides/berlitz1/WhereToItaly.txt
```

* This example looks through the entire "written_2/" directory to find files that are larger than 250 kilobytes. The "+" in the command is to say that the results should be bigger than the given value, "250" is obviously the given numerical value, and "k" is the character used to declare that the the number should be interpreted to be in kilobytes
* By running this command, it is easy to tell what the largest programs in the directory is, given that only two of the many files are larger than 250 KB. Now it is easy to tell where the most data might be stored and what type of similar files might also be larger compared to others.

```
$ find written_2/ -size -2000c -type f
written_2/non-fiction/OUP/Abernathy/custom-file.txt
written_2/travel_guides/berlitz1/HandRHongKong.txt
written_2/travel_guides/berlitz1/HandRIbiza.txt
written_2/travel_guides/berlitz1/HandRIstanbul.txt
written_2/travel_guides/berlitz1/HandRJerusalem.txt
written_2/travel_guides/berlitz1/HandRLakeDistrict.txt
written_2/travel_guides/berlitz1/HandRLasVegas.txt
written_2/travel_guides/berlitz1/HandRLisbon.txt
written_2/travel_guides/berlitz1/HandRLosAngeles.txt
written_2/travel_guides/berlitz1/HandRMadeira.txt
written_2/travel_guides/berlitz1/HandRMallorca.txt
```

* This example does a similar search as above, but instead looks for files that are smaller than 2000 bytes. The "-" is to signify that the file should be smaller than the given value and the "c" is the character used to signify that the number is in bytes. This function uses the `-type` option to make sure that the folders themselves are not included in the search.
* This search tells the user which files are the absolute smallest in the directory. This could mean that if someone is trying to do a quick read, those files should be relatively smaller and thus easier to fully get through. It is easy to tell from the pattern that "HandR" files tend to not include that much data.

For more examples and where this info was found, go here: [https://linuxhandbook.com/find-command-examples/](https://linuxhandbook.com/find-command-examples/)

---

## Executing commands: `find -exec`

Sometimes, when looking for files, you are looking for them with the intent to then run it in some form of command to get more detailed information out of it. Using the `-exec` option with find allows you to do just that, run a certain command on all of the found files. This option makes it possible to have the files found and tested all on one line instead of having to store the info multiple times or constantly passing it off.

```
$ find written_2/ -type f -exec grep -l "Lucayans" {} +
written_2/travel_guides/berlitz2/Bahamas-History.txt
```

* This command finds all of the files within the "written_2/" directory, then looks for the term "Lucayans" in the files, and if the term is present, it returns the file path of where it was found. The info about `grep -l` can be found on Lab Report 3. The "{}" refers to all the files that were found in the `find` command to run the `grep` command on and the "+" is used to indicate the end of the command.
* This is one of many ways to search for files that contain a certain phrase, but it is interesting to know how to do it with `find` as that is the command known best for having a recursive functionality as the default.

```
$ find written_2/ -name "custom-file.txt" -exec rm {} +
```

* This command is different as it provided zero output for the user to see. In this command, the terminal looked within everything in "written_2/" to find something called "custom-file.txt" that was added in to the directory as an experiment but no longer serves a purpose. The command provided on wherever the file was found was `rm` which is used to delete the file. So once the `find` command got the correct file found, it removed it from the directory, hence why there is no ouput as there is nothing left.
* This command can be useful when you know there is a file somewhere in the directory but are not sure where it is located. This saves the user the time to go searching through the entire directory and can just delete the file as long as you know what the name you are looking for is. There is also variations of this to delete all ".class" files or any other type of situation where you want to get rid of unknown files where you have some characteristic to get rid of them.

For more examples and where this info was found, go here: [https://linuxhandbook.com/find-command-examples/](https://linuxhandbook.com/find-command-examples/)

---

`find` is an extremely useful command whose recursive functionality makes it extremely easy to find aspects of a file structure quickly. These four options just add even more function and efficiency to complete more specific tasks quickly, and that is knowledge that can be quite useful when stuck at a problem.
