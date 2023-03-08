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
