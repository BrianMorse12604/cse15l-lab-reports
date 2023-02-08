# Lab Report 3

The command-line has many commands that are extremely useful to utilize to accomplish many goals, from creating directories to manipulating and reading files and more. Some of these basic commands include: `find` which gives files and subdirectories of a given directory, `cat` which prints out the contents of a file, `wc` which gives details about how many lines, words, and characters are in files, and `grep` which searches for a certain term in files. This lab report is going to focus on `grep` and how some different options can change its behavior to solve different problems.

---

## 1. Recursive capabilities: `grep -R`

One extremely useful option to apply to `grep` is to have it search through a directory recursively in case you do not know exactly where a file may be stored. This can be accomplished with the `-R` option so that, when given a directory or file, it will try to go to any subdirectories or files and check for the provided pattern. This way, you can create a much wider search over a directory for what you are looking for instead of having to type every file you want checked within a large directory, which can be a hassle. Here are some displays of the use of this recursive option:

```
$ grep -Rl "Lucayans" written_2/
written_2/travel_guides/berlitz2/Bahamas-History.txt
```

* It can be noticed that not only was `-R` used, but the `-l` option that was used in a previous lab. The command was still searching recursively, but it just returned the file path that the pattern was found in instead of the string, which is the purpose of `-l`.
* The command took the directory `written_2/` and went into every folder and file that could be found in said directory and searched for the pattern "Lucayans", which was evidently found in `Bahamas-History.txt`. 
* This is useful since now the user knows exactly which directory and file to go to in order to find more information about Lucayans.

```
$ grep -Rl "Hong Kong" written_2/
written_2/non-fiction/OUP/Abernathy/ch1.txt
written_2/non-fiction/OUP/Abernathy/ch15.txt
written_2/travel_guides/berlitz1/HandRHongKong.txt
written_2/travel_guides/berlitz1/HandRJamaica.txt
written_2/travel_guides/berlitz1/HistoryHongKong.txt
written_2/travel_guides/berlitz1/IntroHongKong.txt
written_2/travel_guides/berlitz1/WhatToHongKong.txt
written_2/travel_guides/berlitz1/WhatToMalaysia.txt
written_2/travel_guides/berlitz1/WhereToHongKong.txt
written_2/travel_guides/berlitz1/WhereToIndia.txt
written_2/travel_guides/berlitz1/WhereToMalaysia.txt
written_2/travel_guides/berlitz2/Beijing-WhatToDo.txt
written_2/travel_guides/berlitz2/California-WhereToGo.txt
written_2/travel_guides/berlitz2/Canada-WhereToGo.txt
written_2/travel_guides/berlitz2/China-History.txt
written_2/travel_guides/berlitz2/China-WhereToGo.txt
```
* Once again the `-l` option was used for the sake of readability of the output of the command. Clearly there are many files that talk about or at least mention Hong Kong so it becomes extremely cluttered if every long line was printed alongside it. However, for more information, the user can now look more into each of those file paths in order to learn more
* The first example could be used for a very specified search to find a lost file, while this example is more pertaining to finding a general idea of where to do some research to learn more about a subject, like searching a library catalog for a topic you are interested in instead of looking at each book.

For more examples and where this info was found, go here to #13: [https://www.geeksforgeeks.org/grep-command-in-unixlinux/](https://www.geeksforgeeks.org/grep-command-in-unixlinux/) 

---

## 2. Case Sensitivity: `grep -i`

Sometimes writers may not be always accurate with the capitalization of the words they type. Or the only appearance of a word may be at the start of a sentence and is thus capitalized and not all lowercase. Whatever the situation is, being able to ignore case sensitivity can sometimes be useful to get all instances of where a string is located. This is what the `-i` option does to `grep`, it allows the command to ignore the difference between uppercase and lowercase letters and instead just focus on if the term is the same. Here are some displays of the case insensitive search:

```
$ grep -i "beach" written_2/travel_guides/berlitz1/HandRHawaii.txt 
        Mauna Kea Beach Hotel $$$$ 62-100 Kaunaoa Drive, Kohala
        880-3112; <www.maunakeabeachhotel.com>. Built in 1965 by Laurance
        resorts, with a vast art collection, a great beach, a major golf
        lanais face the beach and an atrium complex of gardens and pools in
        Outrigger Waikoloa Beach $$$ 69-275 Waikoloa Beach Drive,
        full-service resort fronts a tremendous swimming and snorkeling beach
        but they come with complete kitchens, a white-sand beach with tide
        Kauai Marriott Resort & Beach Club $$$$ Kalapaki Beach,
        the best hotel pools and swimming beaches in Hawaii. 419 rooms.
        Kepuhi Beach, drive to 3-mile-long Papohaku Beach. 120 rooms.
        camp right on the beach. Outdoor activities run the gamut: horseback
        Lanai’s finest beach (Hulopoe), the Manele Bay Hotel offers water
```
* In this example, only the `-i` option is utilized to search a single file, trying to inquire on some information about a beach in Hawaii
* As displayed in this example, case insensitivity was important as many times when beach is capitalized it referred to a name of a certain beach, instead of just the general concept of the word. Without the case insensitivity, the `grep` command would not have picked up on these details within the file

```
$ grep -Ri "hotel with" written_2/
written_2/travel_guides/berlitz1/HandRHawaii.txt:        western Maui oceanfront resorts, the Ritz-Carlton is a grand hotel with
written_2/travel_guides/berlitz1/HandRIsrael.txt:        4174. A popular, well-located hotel with helpful staff, swimming pool,
written_2/travel_guides/berlitz1/HandRMadrid.txt:        hotel within the city walls. It occupies a 16th-century mansion, with
written_2/travel_guides/berlitz1/WhatToEgypt.txt:        Book a hotel with a pool, so that after a day sightseeing,
written_2/travel_guides/berlitz2/Bahamas-WhereToGo.txt:After a visit to the tower, return to the compact town center. Stroll along any street and you’ll bump into fine historic buildings; several date from the late 1700s and most are painted in pretty pastels that cheerfully reflect the bright Bahamian sunlight. Pink-and-white Balcony House on Market Street is a particularly fine example. The oldest wooden house on the island — it was built by shipwrights around 1790 of American soft cedar — it has been restored and is now a museum that offers a delightful view of life in well-to-do Nassau in the 18th century. Once a private home visited by the likes of the Duke of Windsor and Winston Churchill, Graycliff Mansion on West Hill Street is now a fine hotel with a well regarded menu and wine list. Many of the original Georgian Colonial features have been retained, and a collection of photographs provide guests and visitors with a glimpse into the building’s genteel past.
written_2/travel_guides/berlitz2/Bahamas-WhereToGo.txt:Today Paradise Island may be close to fulfilling the dream of the perfect vacation playground. It has many of the essential ingredients needed: fine white-sand beaches, a protected marina, a golf course, a group of fine hotels, and perhaps the biggest adult playground this side of Las Vegas. The brainchild of the Sol Group, Atlantis Paradise Island is a new concept in resorts — it’s a huge hotel with an amazing theme park and entertainment village all on one site. The resort takes its name, and inspiration, from the lost city of Atlantis, said by some to lie off the coast of Bimini. This theme runs throughout the whole resort. The vast open foyers and public areas of the hotel have high columns of cathedral-like dimensions; the walkways and outside terraces recall Mayan temples, with large stones covering the façade. Waterfalls literally or figuratively cascade to give a feeling of a city just having risen from the ocean. Man-made sheltered lagoons provide for safe swimming, snorkeling, and sunbathing.
written_2/travel_guides/berlitz2/Bahamas-WhereToGo.txt:Disney Cruises run from Port Canaveral, stop at Nassau for a day, and then move on to Disney’s private Bahamian hideaway, “Castaway Cay,” for days of fun and relaxation. Cruises can be combined in packages that include time at Walt Disney World theme park and a Disney hotel within the park.
written_2/travel_guides/berlitz2/Budapest-WhereoGo.txt:The view west from Fishermen’s Bastion focuses on the startling, six-storey reﬂective façade of the Budapest Hilton Hotel. The bold approach of shamelessly merging ancient and modern has integrated the 1977 Hilton Hotel with the remains of a 17th-century Jesuit college and the tower of the district’s oldest church, dating from the 13th century.
```

* The recursive option was used alongside the case insensitivity option in order to look in all the files in `written_2/` for a description about a hotel that presumably would go on to describe some benefits or information about items pertaining to that hotel.
* While there are many instances in this output that has an exact match with case sensitivity to "hotel with", there are instances where case insensitivity was important. For example, in the file `Budapest-WhereoGo.txt`, the string "Hilton Hotel with" can be found within the file. This would not have been included if the command was to only allow the lowercase hotel form to be matching, demonstrating how case insensitivity can be useful in finding the most amount of results within a directory.

For more examples and where this info was found, go here to #1: [https://www.geeksforgeeks.org/grep-command-in-unixlinux/](https://www.geeksforgeeks.org/grep-command-in-unixlinux/)
