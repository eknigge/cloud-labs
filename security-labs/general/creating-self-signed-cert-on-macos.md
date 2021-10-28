# Creating A Self-Signed Certificate On Mac OS X

> Hands-on Lab

|                   |                       |
| :---------------- | :-------------------- |
| Operating System  | **MacOS**   |
| Proficiency Level | **Cloud  Enthusiast** |
| Tags              | ![https://img.shields.io/badge/%20-Certificates-blue](https://img.shields.io/badge/%20-Certificates-blue) |

## Lab Scenario

In this lab, you will create a self-signed certificate using Mac OS X.

Each exercise below builds upon the previous one. You should start each new exercise from the last step of the previous exercise unless it is explicitly written otherwise.

## What will you learn in this lab?

After completion of this lab, you will be able to:

- Create a self-signed certificate on Mac OS X.

## Prerequisites

To complete this lab, you will need the following:

- Macintosh computer with Mac OS X installed.

## Lab Instructions

### Exercise #1: Create a Self-Signed Certificate

In this exercise, you will create a self-signed certificate using Mac OS X Terminal.

1. Press the *Command (⌘)* + *Space* keys on your Mac to show the *Spotlight Search* box.
2. Type `Terminal`*` in the box.
3. Double-click on the *Terminal.app* from the list.
4. When the *Terminal* app starts, create a new directory by typing:
  ```
  mkdir Certificates
  ```
5. Change to the new directory by typing:
  ```
  cd Certificates
  ```
6. Type the following command to start the process of a self-signed certificate creation:
  ```
  openssl req -x509 -days 365 -newkey rsa:4096 -keyout [your_name]-self-signed.key -out [your_name]-self-signed.key.crt
  ```
  
  where you replace `[your_name]` with your first and last name separeted with underscore (`_`).
7. Type a strong password for the certificate.
8. Fill in the following information at the prompts:
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
  ls -al
  ```

#### Exercise Summary

At this point, you have learned how to create a self-signed certificate on Mac OS X.

### Exercise #2: Convert the Self-Signed Certificate to PKCS#12

In this exercise, you will convert the certificate to PKCS#12 format using Mac OS X Terminal. This format is used for upload to cloud-based services and Web servers.

1. Type the following command to convert the certificate to PKCS#12 format
  ```
  openssl pkcs12 -export -in [your_name]-self-signed.key.crt -inkey [your_name]-self-signed.key -out [your_name]-self-signed.key.pfx
  ```
2. List the files in the folder using the following command:
  ```
  ls -al
  ```

#### Exercise Summary

At this point, you have learned how to convert the self-signed certificate to PKCS#12 format on Mac OS X.

#### Exercise Summary

At this point, you have learned how to convert the self-signed certificate from PKCS#12 format to PEM format on Mac OS X.

## Help improve this lab

[![Lab Issues](https://img.shields.io/github/issues/crimsonpinnacle/cloud-labs)](https://github.com/CrimsonPinnacle/cloud-labs/issues/new?assignees=toddysm&labels=new+lab&template=bug_template.md&title=) [![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/CrimsonPinnacle/cloud-labs/pulls)