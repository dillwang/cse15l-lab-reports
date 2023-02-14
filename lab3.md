# Lab Report 3
# command-line options for `grep`
---
# `-i`

* `grep -i` allows users to perform case-insensitive search in which upper and lower case letter does not matters.

* Source: https://www.geeksforgeeks.org/grep-command-in-unixlinux/

* Example 1:
```
grep -i "hotel" HandRHongKong.txt
```

![Image](StringAdd2.png)

This command finds all lines that contains the string "hotel" in file "HandRHongKong.txt" and returns them. It will returns all "hotel" lines even if they contains any upper case letters or other words. It is useful in this case because user can find all "hotel" in this file no matter if they are uppercased or in plural form because of certain grammer convention.

* Example 2:
```
grep -i "city" HandRIsrael.txt
```

![Image](StringAdd2.png)

This command finds all lines that contains the string "city" in file "HandRIsrael.txt" and returns them. It will returns all "city" lines even if they contains any upper case letters or other words. It is useful in this case because user can find all "city" in this file no matter if they are uppercased or in plural form because of certain grammer convention.

---

# `-r`

* `grep -r` allows users to search recursively through the directories.

* Source: https://www.tutorialspoint.com/unix_commands/grep.htm

* Example 1:
```
grep -r "implementation" Abernathy
```

![Image](StringAdd2.png)

This command search recursively through all files in directory "Abernathy" and finds all lines in files that contain the string "implementation" in them. This is very useful in searching large amount of files in the same directory or sub-directories because user will not have to apply the normal `grep` command on each individual file.

* Example 2: 
```
grep -r "revolution" ch1.txt
```

![Image](StringAdd2.png)

This command search recursively through file "ch1.txt" and finds all lines in this file that contain the string "revolution" in it. When applying `grep -r` on a single file, it function as a normal `grep` command. This produce the same result as using `grep -r` on a directory that has only 1 file in it. 

---

# `-c`

* `grep -c` allows users to count the number of lines that match the pattern.

* Source: https://www.baeldung.com/linux/grep-command

* Example 1:
```
grep -c "American" ch1.txt
```

![Image](StringAdd2.png)

This command counts the number of times that "American" appeared inside "ch1.txt." It is useful when the user only want to know how many times the word appeared in the file without actually getting the the lines that contains the word. It simplifies the process of using `grep` and then `wc` to find the number of times it appears.

* Example 2:
```
grep -c "store" ch3.txt
```

![Image](StringAdd2.png)

This command counts the number of times that "store" appeared inside the "ch3.txt." It is useful when the user only want to know how many times the word appeared in the file without actually getting the the lines that contains the word. It simplifies the process of using `grep` and then `wc` to find the number of times it appears.

---

# `-rl`

* `grep -rl` only prints the names of files that match the pattern within a directory.

* Source: https://www.gnu.org/software/grep/manual/grep.html#General-Output-Control

* Example 1:
```
grep -rl "American" Abernathy
```

![Image](StringAdd2.png)

This command return all files in directory `Abernathy` that contains the string "American" in their content. It combine the function of `-r` which recursively go through all files in the current working directory and all its sub-directories and then find the patterns that match the input. Then, `-l` return user the name of the file instead of returning the line that contains the pattern.

* Example 2:
```
grep -rl "luxury" berlitz2
```

![Image](StringAdd2.png)

This command return all files in directory `berlitz2` that contains the string "luxury" in their content. It combine the function of `-r` which recursively go through all files in the current working directory and all its sub-directories and then find the patterns that match the input. Then, `-l` return user the name of the file instead of returning the line that contains the pattern.
