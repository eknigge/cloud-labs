# Creating A Static Website In Amazon S3

> Hands-on Lab

|                   |                       |
| :---------------- | :-------------------- |
| Cloud Vendor      | **Amazon AWS**        |
| Proficiency Level | **Cloud  Enthusiast** |
| Tags              | ![https://img.shields.io/badge/%20-S3-blue](https://img.shields.io/badge/%20-S3-blue) ![https://img.shields.io/badge/%20-Storage-blue](https://img.shields.io/badge/%20-Storage-blue) ![https://img.shields.io/badge/%20-Web%20Server-blue](https://img.shields.io/badge/%20-Web%20Server-blue) |

## Lab Scenario

In this lab, you will provision an Amazon S3 bucket and create a static website in it. You will upload static web pages and images to the bucket that is used for the static web site and will test that the content is served properly.

Each exercise below builds upon the previous one. You should start each new exercise from the last step of the previous exercise unless it is explicitly written otherwise.

## What will you learn in this lab?

After completion of this lab, you will be able to:

- Provision an Amazon S3 Bucket.
- Create a static website in the newly provisioned Amazon S3 Bucket.
- Upload content to the static website.
- Test the static web site.
- Delete the Amazon S3 Bucket.

## Prerequisites

To complete this lab, you will need the following:

- Reliable internet connection.
- A free AWS Account used to access the AWS Management Console.

## Lab Instructions

### Exercise 1: Exercise Title

In this exercise, you will create an Amazon S3 bucket that you will use to host your static web site.

1. Sign into the AWS Management console at [https://aws.amazon.com/console/](https://aws.amazon.com/console/) using your AWS credentials.
2. In the search box on top of the screen, type *S3* and press *Enter*.
3. Click on *S3* from the list of *Services*.
4. On the *Amazon S3* page, click on the ![Create bucket button](media/aws-create-bucket-orange-button.png) button.
5. Fill in the following information on the *Create bucket* page:
   - *Bucket name* → `[initials]s3sitelabbkt`, where `[initials]` are your initials
   - *Region* → `US West (Oregon) us-west-2`
6. Remove the check in front of `Block all public access` and acknowledge the warning.
7. Select `Disable` for *Bucket Versioning*.
8. Click on the ![Add tag button](media/aws-add-tag-button.png) and add the following tags:
   - *Role* → `static web`
   - *Lab* → `s3storagelab`
   - *Owner* → `[your name]`
   - *OwnerEmail` → `[your email]`
9. Select `Disable` for *Default encryption*.
10. Click on the ![Create bucket button](media/aws-create-bucket-orange-button.png) button.
 
#### Exercise Summary

At this point, you have learned how to create an Amazon S3 bucket.

### Exercise #2: Enable Static Website in Amazon S3 Bucket

In this exercise, you will enable the hosting of a static website in the Amazon S3 bucket.

1. Clik on the `[initials]s3sitelabbkt` bucket from the list, where `[initials]` are your initials.
2. On the next screen, change to the *Permissions* tab.
3. Scroll down to the *Static website hosting* section and click on the ![Edit button](media/aws-edit-button.png).
4. Change the selection to `Enable`.
5. Fill in the following information in the form that appears:
   - *Index document* → `index.html`
   - *Error document* → `error.html`
6. Click on the ![Save changes button](media/aws-save-changes-orange-button.png) button.
7. Scroll down to the *Static website hosting* section and copy the *Bucket website endpoint* URL.
8. Open a new browser window, paste the copied URL into the address bar, and press *Enter*.

#### Exercise Summary

At this point, you have learned how to enable a static web site hosting in your Amazon S3 Bucket and access it via the browser.

### Exercise #3: Upload Content to the Static Website in Amazon S3

In this exercise, you will upload content to the static website.

1. Create a new file on your local machine with name `index.html` and the following content:
   ```
    <!DOCTYPE html>
    <html>
        <head>
            <title>Welcome to Amazon S3</title>
        </head>
        <body>
            <h1>My Static Website</h1>
            <p>Hello, I am a static web site hosted in Amazon S3 Bucket.</p>
        </body>
    </html>
   ```
2. Create a new file on your local machine with name `error.html` and the following content:
   ```
    <!DOCTYPE html>
    <html>
        <head>
            <title>Ooops... error!</title>
        </head>
        <body>
            <h1>An error occured</h1>
            <p>Ooops, it seems that we encountered an error or you are trying to access the wrong page.</p>
        </body>
    </html>
   ```
3. Take a screenshot of the text editor you used to create the above two files and save it on your local machine with the following name `ide-screenshot.png`.
4. In the AWS Management Console switch to the *Objects* tab for your bucket.
5. Click on the ![Upload button](media/aws-upload-button.png) button.
6. On the *Upload* screen, click on the ![Add files button](media/aws-add-files-button.png) button.
7. Select the files from your local machine and upload them to the bucket.
8. Expand the *Permissions* section, and select `Grant public-read access`
9. Click on the ![Upload button](media/aws-upload-button.png) button.
10. Once the files are uploaded, click on the ![Close button](media/aws-close-button.png) button.
11. Select all uploaded files and click on the ![Actions dropdown button](media/aws-actions-dropdown-button.png) dropdown button.
12. Select `Make public` from the list.
13. Click on the ![Make public button](media/aws-make-public-button.png) button.
14. Click on the ![Close button](media/aws-close-button.png) button.
15. Reload the URL from step 8 in exercise 2.
16. Add the following `/foo` to the end of the URL in your browser’s address bar and press *Enter*.
17. Remove the `/foo` from the URL in your browser’s address bar and add the following `/ide-screenshot.png`.
18. Press *Enter*.

#### Exercise Summary

At this point, you have learned how to access the home page of the static web site you created in your S3 Bucket. You have also learned how the static web site you created in your S3 Bucket handles errors and binary content like images.

### Exercise #4: Delete the Amazon S3 Bucket

In this exercise, you will delete the Amazon S3 Bucket to save costs.

1. Select all files that you uploaded in exercise 3.
2. Click on the ![Delete button](media/aws-delete-button.png) button above the list.
3. Confirm the deletion by filling in the required information in the text box and clicking on the ![Delete objects](media/aws-delete-objects-orange-button.png) button.
4. Click on the ![Close button](media/aws-close-button.png) button.
5. Click on *Amazon S3* in the breadcrumbs on top of the page.
6. Select the `[initials]s3sitelabbkt` bucket from the list.
7. Click on the ![Delete button](media/aws-delete-button.png) button above the list.
8. Type the name of the bucket and click on the ![Delete bucket button](media/aws-delete-bucket-orange-button.png) button.
 
#### Exercise Summary

At this point, you have learned how to delete your Amazon S3 Bucket to save cost.

## Help improve this lab

[![Lab Issues](https://img.shields.io/github/issues/crimsonpinnacle/cloud-labs)](https://github.com/CrimsonPinnacle/cloud-labs/issues/new?assignees=toddysm&labels=new+lab&template=bug_template.md&title=) [![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/CrimsonPinnacle/cloud-labs/pulls)