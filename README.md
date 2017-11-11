# Simple Firebase Cloud Functions and Send Mail- Database triggers
Firebase cloud functions database triger and send mail

## Introduction

We'll deploy firebase triggered Functions that send a welcome email when a new child added. 
Why we are not using Auth triggered, the first reasone is firebase had made it. [Here the link](https://github.com/firebase/functions-samples/tree/master/quickstarts/email-users).
the second is sometimes our user have diffrent level, so when we want to send diffrent email when we have new user, Auth triggered can't handle it (That's what I know now). 

Further reading: [Firebase SDK for Cloud Functions](https://firebase.google.com/docs/functions/)

In this example we will use gmail for our SMTP service. Be aware that Gmail has an [email sending quota](https://support.google.com/mail/answer/22839). You can use another SMTP service for sending a large number of emails.for sending email, exampe : [Sendgrid](https://console.cloud.google.com/launcher/details/sendgrid-app/sendgrid-email), [Mailjet](https://www.mailjet.com/google) or [Mailgun](http://www.mailgun.com/google) 

## Setting up the sample

 1. Create a Firebase Project using the [Firebase Console](https://console.firebase.google.com).
 1. Install Firebase CLI `npm install -g firebase-tools` and then configure it with `firebase login`.
 1. Configure the CLI locally by using `firebase use --add` and select your project in the list.
 1. Install Cloud Functions dependencies locally by running: `cd functions; npm install; cd -`
 1. To be able to send emails with your Gmail account: enable access to [Less Secure Apps](https://www.google.com/settings/security/lesssecureapps) and [Display Unlock Captcha](https://accounts.google.com/DisplayUnlockCaptcha). For accounts with 2-step verification enabled [Generate an App Password](https://support.google.com/accounts/answer/185833).
 1. Set the `gmail.email` and `gmail.password` Google Cloud environment variables to match the email and password of the Gmail account used to send emails (or the app password if your account has 2-step verification enabled). For this use:

    ```bash
    firebase functions:config:set gmail.email="myusername@gmail.com" gmail.password="secretpassword"
    ```
 

## Deploy and test

This sample comes with a web-based UI for testing the function. To test it out:

 1. Deploy your project using `firebase init` and choose google cloud function
 1. Deploy your project using `firebase deploy`
 1. Open the app using `firebase open hosting:site`, this will open a browser.
 1. Try add new child in your database `users`. The example like this : 
 `{
   "123123" : {
    "displayName" : "Cakra Danu Sedayu",
    "email" : "cakra.ds@gmail.com"
    }
}`

