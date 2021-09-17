# Exploring PowerShell

> Hands-on Lab

|                   |                       |
| :---------------- | :-------------------- |
| Operating System  | **Microsoft Windows** **Mac OS** **Linux** |
| Proficiency Level | **Cloud  Enthusiast** |
| Tags              | ![https://img.shields.io/badge/%20-PowerShell-blue](https://img.shields.io/badge/%20-PowerShell-blue) |

## Lab Scenario
The objective of this lab is to get familiar with Windows PowerShell. At the end of this lab, you will be able to start the PowerShell command line interface, list the cmdlets available on your machine and get the help of specific cmdlet.

## Prerequisites
If you are MacOS or Linux user, you will need the install PowerShell on your machine. Select the appropriate instructions from the list below:

- [Installing PowerShell on macOS](https://docs.microsoft.com/en-us/powershell/scripting/install/installing-powershell-core-on-macos).
- [Installing PowerShell on Linux](https://docs.microsoft.com/en-us/powershell/scripting/install/installing-powershell-core-on-linux).

## Lab Instructions

1. Start PowerShell on your machine. This will open terminal window and show the prompt.
2. Type `Get-Command` after the prompt.
3. You will receive a list of all PowerShell cmdlets installed on your machine. If you have many cmdlets installed the screen will scroll.
4. Type `Get-Command | more` after the prompt.
5. You will receive a list of all PowerShell cmdlets installed on your machine. When the screen fills in, the scrolling will stop and wait for you to press space to continue to the next page or q to exit the list.
6. *Milestone step:* At this point, you have learned how to list PowerShell cmdlets and control the paging of the long list.
7. Type `Get-Help Write-*` after the prompt.
8. You will receive a list of cmdlets that start with `Write-`.
9. Type `Get-Help Write-Host` after the prompt.
10. You will receive help information about the `Write-Host` cmdlet.
11. *Milestone step:* At this point, you have learned how to filter the list of PowerShell cmdlets and receive help for the specific cmdlet.

## Help improve this lab

[![Lab Issues](https://img.shields.io/github/issues/crimsonpinnacle/cloud-labs)](https://github.com/CrimsonPinnacle/cloud-labs/issues/new?assignees=toddysm&labels=new+lab&template=bug_template.md&title=) [![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/CrimsonPinnacle/cloud-labs/pulls)