# Using Command Prompt on Windows

> Hands-on Lab

|                   |                       |
| :---------------- | :-------------------- |
| Operating System  | **Microsoft Windows** |
| Proficiency Level | **Cloud  Enthusiast** |
| Tags              | ![https://img.shields.io/badge/%20-Windows-blue](https://img.shields.io/badge/%20-Windows-blue) ![https://img.shields.io/badge/%20-Command%20Prompt-blue](https://img.shields.io/badge/%20-Command%20Prompt-blue) |

## Lab Scenario
The objective of this lab is to get familiar with Windows Command Prompt. At the end of this lab, you will be able to start the Command Prompt program, know your user’s home folder, navigate the directory tree, browse files and create and save text files with Notepad.

## Lab Instructions

1. Click on the **[Start]** button and type *Command prompt*.
2. Click on the **[Command prompt]** desktop app from the list.
3. *Milestone step:* At this point, you have learned how to start *Command Prompt* on a Windows machine.
4. In the Command Prompt window, note the path shown. Should be in the form: `C:\Users\{your-username}>`.
5. *Milestone step:* At this point, you have learned what is the path to the home folder for your user on your Windows machine.
6. Type the `dir` command after the prompt `>`:
   ```
   C:\Users\{your-username}> dir
   ```
7. You will receive the list of files in your home folder.
8. *Milestone step:* At this point, you have learned how to list files in a folder on a Windows machine.
9. Type `notepad test.txt` after the prompt `>`:
   ```
   C:\Users\{your-username}> notepad test.txt
   ```
10. Confirm the creation of the `test.txt` file by clicking on the **[Yes]** button.
11. Type your name in the file and select **[File]** → **[Save]**.
12. Click on the **X** in the upper right corner of the Notepad window.
13. *Milestone step:* At this point, you have learned how to create a new text file and edit it with Notepad.
14. Type `dir test.*` after the prompt `>`:
    ```
    C:\Users\{your-username}> dir test.*
    ```
15. You will receive a list of files that start with a test.
16. *Milestone step:** At this point, you have learned how to list file using basic filtering criteria.
17. Type `more test.txt` after the prompt `>`:
    ```
    C:\Users\{your-username}> more test.txt
    ```
18. You will see the content of the file `test.txt`.
19. *Milestone step:* At this point, you have learned how to see the content of a text file without opening it in an editor.
20. Type `cd ..` after the prompt `>`:
    ```
    C:\Users\{your-username}> cd ..
    ```
21. You will end up one level up in the directory tree.
22. Type `cd {your-username}` after the prompt `>`:
    ```
    C:\Users> cd {your-username}
    ```
23. You will go back to your home folder.
24. *Milestone step:* At this point, you have learned how to navigate the directory tree using Command Prompt on your Windows machine

## Help improve this lab

[![Lab Issues](https://img.shields.io/github/issues/crimsonpinnacle/cloud-labs)](https://github.com/CrimsonPinnacle/cloud-labs/issues/new?assignees=toddysm&labels=new+lab&template=bug_template.md&title=) [![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/CrimsonPinnacle/cloud-labs/pulls)