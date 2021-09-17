# Using Command Prompt on Windows

> Hands-on Lab

|                   |                       |
| :---------------- | :-------------------- |
| Operating System  | **MacOS** |
| Proficiency Level | **Cloud  Enthusiast** |
| Tags              | ![https://img.shields.io/badge/%20-MacOS-blue](https://img.shields.io/badge/%20-MacOS-blue) ![https://img.shields.io/badge/%20-Terminal-blue](https://img.shields.io/badge/%20-Terminal-blue) |

## Lab Scenario
The objective of this lab is to get familiar with MacOS terminal and basic shell commands. You will also learn how to edit a file in the built-in Vi editor. At the end of this lab, you will be able to start the Terminal app, know your user’s home folder, navigate the directory tree, browse files and create and save text files with Vi.

## Lab Instructions


1. Press the `Command key ⌘` + `space` on your Mac keyboard to open *Spotlight Search*.
2. Type `terminal` in the *Spotlight Search* input box and press the *Return* key.
3. *Milestone step:* At this point, you have learned how to start the *Terminal* app in MacOS.
4. In the *Terminal* window type `pwd` after the prompt `%`.
5. You will see the current folder location, which is the home folder of your user on the machine.
6. *Milestone step:* At this point, you have learned what is the path to the home folder for your user on your Mac machine.
7. Type `ls` after the prompt `%`.
8. You will receive the list of non-hidden files and folders in your home folder
9. Type `ls -al` after the prompt `%`.
10. You will receive the list of all files and folders in your home folder in a list form including additional information like type (file or folder), owner, group, size and modification date.
11. *Milestone step:* At this point, you have learned how to list files in a folder on a Mac machine as well as get additional information about the files and folders.
12. Type `vi test.txt` after the prompt `%`.
13. Your terminal window will change to Vi mode and will show `“test.txt” [New File]` at the bottom.
14. *Milestone step:* At this point, you have learned how to open a new file in Vi text editor.
15. Press the `I` key on your keyboard to enter insert mode. You will see `--INSERT--` at the bottom of the screen.
16. Type your first name.
17. Press the `ESC` key on your keyboard to exit insert mode.
18. Use the arrow keys on your keyboard to position the cursor before your name.
19. Press the `I` key on your keyboard to enter insert mode.
20. Type `I am ` before your name.
21. *Milestone step:* At this point, you have learned how to use the insert mode in Vi and move around the cursor.
22. Press the `ESC` key on your keyboard to exit insert mode.
23. Use the arrow keys on your keyboard to position the cursor at the end of your name.
24. Press the `A` key on your keyboard to enter append mode.
25. Type your last name.
26. Press the `ESC` key on your keyboard to exit append mode.
27. Use the arrow keys on your keyboard to position the cursor before your first name.
28. Use the `X` key on your keyboard to delete your first name.
29. Type `:w` in the Vi command line (this is the bottom line of the window).
30. *Milestone step:* At this point, you have learned how to append and delete text in Vi and save your file.
31. Type `:q` in the Vi command line (this is the bottom line of the window).
32. You will exit Vi.
33. Type `ls -al test.*` after the prompt `%`.
34. *Milestone step:* At this point, you have learned how to exit Vi text editor and list the file you have just created in your home folder.
35. Type `cd ..` after the prompt `%`.
36. Type `ls -al` after the prompt `%`.
37. You will be in the `/Users` folder on your Mac machine.
38. Type `cd ../var` after the prompt `%`.
39. You will be in the `/var` folder on your Mac machine.
40. Type `cd ~` after the prompt `%`.
41. *Milestone step:* At this point, you have learned how to navigate the directory structure in MacOS.

## Help improve this lab

[![Lab Issues](https://img.shields.io/github/issues/crimsonpinnacle/cloud-labs)](https://github.com/CrimsonPinnacle/cloud-labs/issues/new?assignees=toddysm&labels=new+lab&template=bug_template.md&title=) [![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/CrimsonPinnacle/cloud-labs/pulls)