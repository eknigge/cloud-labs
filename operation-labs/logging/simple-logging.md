# Implementing Logging in a Python Script

> Hands-on Lab

|                   |                       |
| :---------------- | :-------------------- |
| Proficiency Level | **Cloud  Enthusiast** |
| Tags              | ![https://img.shields.io/badge/%20-Logging-blue](https://img.shields.io/badge/%20-Logging-blue) ![https://img.shields.io/badge/%20-Operations-blue](https://img.shields.io/badge/%20-Operations-blue) ![https://img.shields.io/badge/%20-Python-blue](https://img.shields.io/badge/%20-Python-blue)|

## Lab Scenario

In this lab, you will write a simple Python program and implement detailed logging in it.

## What will you learn in this lab?

After completion of this lab, you will be able to:

- Understand what logging is and the different log levels.

## Prerequisites

To complete this lab, you will need the following:

- Python interpreter installed on your machine.
- Text editor of your choice.

## Lab Instructions

### Exercise #1: Implement a Simple Python Script 

In this exercise you will implement a simle Python script that will accept user input and read from or write to a file. When reading dn writing, you will implement logging and performance metrics for the operations that you perform in your code.

Here are the requirements for the script:

- The script should accept two input parameters:
  - Path to a text file used to read from or write to
  - Read/write switch denoting whether the user action is to read the file or to write to the file
- When the user action is to "read" the file:
  - You should read the file line by line and find the word "imperdiet" in every line
  - The output of the read operation is to:
    - Count how many times the word "imperdiet" exists in the file
    - Count in how many lines the word "imperdiet" appears
- When the user action is to "write" to the file:
  - You should prompt the user to enter a sentence
  - You should look for the character `i` in every sentence entered by the user
  - The output of the "write" action should be:
    - Count how many sentences the user entered
    - Count how many times the character `i` appear in the user input
    - Count in how many sentences the character `i` appeared

While implementing the code, you must also instrument your code for logging and performance as follows:

- You will use Python's logging framework to store log information to the "consoleapp.log" file.   
  - You must have log messages with each of the following levels: CRITICAL, ERROR, INFO, DEBUG, TRACE.
  - You should configure your logging to log with TRACE level but allow for easy reconfiguration to other log levels without code changes.
- You will also need to collect the following performance metrics for your code:
  - Total execution time
  - When in "read" mode
    - Average time to read a line from the file
    - Average time to find all the letters `i` in the line
  - When in "write" mode
    - Average time to write a line in the file
    - Average time to find all the letters `i` in the line
- You should add an additional (administrative) input to the program to allow the user to print the performance statistics after the output

### Exercise #2: Test Your Python Script

In this exercise you will test your Python script and generate the log file and the performance metrics.

1. Go to [https://lipsum.com](https://lipsum.com) and generate 1000 paragraphs of text.
2. Save the generated text in a file on your local machine.
3. Run your script in a "read" mode providing the above file as an input.
4. Save the generated metrics output into a file `metrics-read.txt`.
5. Run your script in a "write" mode and type random text as input. Use multiple sentences for your input.
6. Exit the script and save the generated metrics in a file `metrics-write.txt`

## Help improve this lab

[![Lab Issues](https://img.shields.io/github/issues/crimsonpinnacle/cloud-labs)](https://github.com/CrimsonPinnacle/cloud-labs/issues/new?assignees=toddysm&labels=new+lab&template=bug_template.md&title=) [![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/CrimsonPinnacle/cloud-labs/pulls)