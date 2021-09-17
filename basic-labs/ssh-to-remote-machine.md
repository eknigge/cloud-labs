# Using Command Prompt on Windows

> Hands-on Lab

|                   |                       |
| :---------------- | :-------------------- |
| Operating System  | **Microsoft Windows** **Mac OS** **Linux** |
| Proficiency Level | **Cloud  Enthusiast** |
| Tags              | ![https://img.shields.io/badge/%20-SSH-blue](https://img.shields.io/badge/%20-SSH-blue) ![https://img.shields.io/badge/%20-Shell-blue](https://img.shields.io/badge/%20-Shell-blue) |

## Lab Scenario

The objective of this lab is to connect to a remote machine using SSH and learn basic shell commands. You will also learn how to edit a file using the built-in Vi editor. At the end of this lab, you will be able to connect to a remote machine using SSH, know your user’s home folder, navigate the directory tree, browse files and create and save text files with Vi.

## Prerequisites

If you are Windows 10, MacOS, or Linux user, SSH will be available from the Command Prompt or Terminal. For earlier versions of Windows, you will need to install a third party SSH client.

> **Note:** You will need to have your instructor provide access information to the remote machine. This includes `IP address`, `username`, and `password`.

## Lab Instructions

1. Open SSH client window.
2. Type the following command:
   ```
   ssh computelabadmin@<ip-address-of-the-remote-machine>
   ```
3. Enter the password for the remote machine.
4. *Milestone step:* At this point, you have learned how to connect to a remote machine using SSH.
5. Type `pwd` after the prompt `~`.
6. You will see the current folder location, which is the home folder of your user on the machine.
7. *Milestone step:* At this point, you have learned what is the path to the home folder for your user on the remote machine.
8. Type `ls` after the prompt `~`.
9. You will receive the list of non-hidden files and folders in your home folder.
10. Type `ls -al` after the prompt `~`.
11. You will receive the list of all files and folders in your home folder in a list form including additional information like type (file or folder), owner, group, size and modification date.
12. *Milestone step:* At this point, you have learned how to list files in a folder on a Mac machine as well as get additional information about the files and folders.
13. Type `vi test.txt` after the prompt `~`.
14. Your terminal window will change to Vi mode and will show `“test.txt” [New File]` at the bottom.
15. *Milestone step:* At this point, you have learned how to open a new file in Vi text editor.
16. Press the `I` key on your keyboard to enter insert mode. You will see `--INSERT--` at the bottom of the screen.
17. Type your first name.
18. Press the `ESC` key on your keyboard to exit insert mode.
19. Use the arrow keys on your keyboard to position the cursor before your name.
20. Press the `I` key on your keyboard to enter insert mode.
21. Type `I am ` before your name.
22. *Milestone step:* At this point, you have learned how to use the insert mode in Vi and move around the cursor.
23. Press the `ESC` key on your keyboard to exit insert mode.
24. Use the arrow keys on your keyboard to position the cursor at the end of your name.
25. Press the `A` key on your keyboard to enter append mode.
26. Type your last name.
27. Press the `ESC` key on your keyboard to exit append mode.
28. Use the arrow keys on your keyboard to position the cursor before your first name.
29. Use the `X` key on your keyboard to delete your first name.
30. Type `:w` in the Vi command line (this is the bottom line of the window).
31. *Milestone step:* At this point, you have learned how to append and delete text in Vi and save your file.
32. Type `:q` in the Vi command line (this is the bottom line of the window).
33. You will exit Vi.
34. Type `ls -al test.*` after the prompt `~`.
35. *Milestone step:* At this point, you have learned how to exit Vi text editor and find the file you have just created in your home folder.
36. Type `cd ..` after the prompt `~`.
37. Type `ls -al` after the prompt `~`.
38. You will be in the `/Users` folder on the remote machine.
39. Type `cd ../var` after the prompt `~`.
40. You will be in the `/var` folder on the remote machine.
41. Type `cd ~` after the prompt `~`.
42. *Milestone step:* At this point, you have learned how to navigate the directory structure on the remote machine.
43. Type `exit` after the prompt `~`.
44. This disconnects you from the remote machine.
45. *Milestone step:* At this point, you have learned how to disconnect from the remote machine.

## Help improve this lab

[![Lab Issues](https://img.shields.io/github/issues/crimsonpinnacle/cloud-labs)](https://github.com/CrimsonPinnacle/cloud-labs/issues/new?assignees=toddysm&labels=new+lab&template=bug_template.md&title=) [![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/CrimsonPinnacle/cloud-labs/pulls)