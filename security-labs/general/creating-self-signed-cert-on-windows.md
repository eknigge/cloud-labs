# Creating A Self-Signed Certificate On Windows 10

> Hands-on Lab

|                   |                       |
| :---------------- | :-------------------- |
| Operating System  | **Microsoft Windows 10**   |
| Proficiency Level | **Cloud  Enthusiast** |
| Tags              | ![https://img.shields.io/badge/%20-Certificates-blue](https://img.shields.io/badge/%20-Certificates-blue) |

## Lab Scenario

In this lab, you will create a self-signed certificate using Windows 10.

Each exercise below builds upon the previous one. You should start each new exercise from the last step of the previous exercise unless it is explicitly written otherwise.

## What will you learn in this lab?

After completion of this lab, you will be able to:

- Create a self-signed certificate on Windows 10.

## Prerequisites

To complete this lab, you will need the following:

- PC with Windows 10 installed
- [Git Bash](https://git-scm.com/downloads) installed

## Lab Instructions

### Exercise #1: Create a Self-Signed Certificate

In this exercise, you will create a self-signed certificate using Command Prompt.

1. Press the *Start* button on your PC keyboard and type `Git Bash`.
2. Click on the *Git Bash* application from the list.
3. When the *Command Prompt* app starts, create a new directory by typing:
  ```
  mkdir Certificates
  ```
4. Change to the new directory by typing:
  ```
  cd Certificates
  ```
5. Type the following command to start the process of a self-signed certificate creation:
   ```
   openssl req -x509 -days 365 -newkey rsa:4096 -keyout [your_name]-self-signed.key -out [your_name]-self-signed.key.crt
   ```
   
   where you replace `[your_name]` with your first and last names separated by underscore.
4. Type a strong password for the certificate.
5. Fill in the following information at the prompts:
  - *Country Name (2 letter code)*: `US`
  - *State or Province Name (full name)*: `Washington`
  - *Locality Name (eg, city)*: `Seattle`
  - *Organization Name (eg, company)*: `[your first and last names]`
  - *Organizational Unit Name (eg, section)*: `Home`
  - *Common Name (eg, fully qualified host name)*: `[your_first_and_last_name]-mac`
  - *Email Address*: `[your_email]`
9. Create a decrypted version of your private key using the following command:
  ```
  openssl rsa -in [your_name]-self-signed.key -out [your_name]-self-signed.decrypted.key
  ```
  
  >**Note:** The decrypted version of your private key is not protected with a password. Everyone who can obtain the decrypted private key can used it to sign data and decrypt messages.
10. List the files in the folder using the following command:
  ```
  dir
  ```

#### Exercise Summary

At this point, you have learned how to create a self-signed certificate on Windows 10.

### Exercise #2: Convert the Self-Signed Certificate to PKCS#12
In this exercise, you will convert the certificate to PKCS#12 format using Windows Command Prompt. This format is used for upload to cloud-based services and Web servers.

1. Type the following command to convert the certificate to PKCS#12 format:
  ```
  openssl pkcs12 -export -in [your_name]-self-signed.key.crt -inkey [your_name]-self-signed.key -out [your_name]-self-signed.key.pfx
  ```
2. List the files in the folder using the following command:
  ```
  dir
  ```

#### Exercise Summary

At this point, you have learned how to convert the self-signed certificate to PKCS#12 format on Windows 10.

## Help improve this lab

[![Lab Issues](https://img.shields.io/github/issues/crimsonpinnacle/cloud-labs)](https://github.com/CrimsonPinnacle/cloud-labs/issues/new?assignees=toddysm&labels=new+lab&template=bug_template.md&title=) [![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/CrimsonPinnacle/cloud-labs/pulls)