# Delivery Email Function

When new data is added to a Firebase Database, this function will be triggered to send an email message to a specific email address using your google email.

# To do

* [Allow less secure apps on your google account](https://support.google.com/accounts/answer/6010255?hl=en)
* Create a database on Firebase.
* Create a cloud function on Firebase.
* Change the constant **emailToSendMsg** value in the **index.js** with your email address.
* Open the terminal and launch the following command to store your google credentials in your function ```firebase functions:config:set gmail.login=yourlogin@gamail.com gmail.pass=yourpass```. These credentials will be stored in the following variables:

    * ```const gmailEmail = functions.config().gmail.login;```
    * ```const gmailPassword = functions.config().gmail.pass;```

* In the following code change **formsubmit** with your database name:

```javascript
//.onDataAdded is watches for changes in database
exports.onDataAdded = functions.database.ref('/formsubmit/{sessionId}').onCreate(function (snap, context) {

    //here we catch a new data, added to firebase database, it stored in a snap variable
    const createdData = snap.val();

    //here we send new data using function for sending emails
    return goMail(createdData);
});
```

* Deploy the code to your Firebase Cloud Function.

# Built with:

* [Nodemailer](https://nodemailer.com/about/)
* [Firebase](https://firebase.google.com/)
* [Nodejs](https://nodejs.org/en/)