#### Version
_*(required)*_ - indicates what command packet version is used
  * value: 1.6

```json
"version": "1.6"
```
#### Type
 _*(required)*_ - indicates the type of communication the command packet is being submitted for

* value: print | email | pdf | sms

```json
"type": "email"
```

#### Authentication
_*(required)*_ - authenticates the sender of the command packet

* **sponsorkey**:  _*(required)*_ - provided following on-boarding
* **clientkey**:  _*(required)*_ - provided following on-boarding

```json
"authentication": {
  "sponsorkey": "0a3c5aad8cfb496eae7966339a024965",
    "clientkey": "DEMO6661549e4aa9811754bb29880cc9",
}
```

#### Email
* _*(required for email sending)*_ - email sender information
    *   **subject**:  *(required)* - subject line of the email
    *   **from**: *(required)*
      * **name**:  *(required)* - sender's name
      * **email**:  *(required)* - sender's email

```json
"email": {
  "subject": "Demo Email",
      "from" : {
        "name": "John Public",
      "email": "john.public@velma.com"
       }
}
```
#### User
_*(required)*_ - this is a variable field area with replacement token values
    (The goal of this area is for it to be any tokens that are to be used inside the product html and operating against the [command packet token system](https://readme.velma.io/#1ca90d39-9082-48f9-a84a-5947e139b7eb))

  * **appuniqueid** - _*(required)*_ - a reference sponsor id that uniquely identifies the user.<br>
   The other fields can be anything you want to replace in your product.

```json
"user": {
     "appuniqueid": "2456",
     "firstname": "John",
     "lastname": "Public",
     "title": "Loan Officer",
     "nmls": "1234321",
     "office telephone": "555-5555",
     "cell telephone": "555-5551",
     "company": "CO Public ",
     "address1": "5465 COPublic Way",
     "city": "Boise",
     "state": "Idaho",
     "zip": "83646",
     "personalphoto": "https://urllocation/personalphoto.jpg",
     "businesslogo": "http://urllocation/publicCo.jpg",
     "disclaimer": "My Disclaimer"
 }
```
#### Product
_*(required)*_ - This is the id of the library piece that will be fetched, tokenized and sent to the contact.<br>

* **id**:  _*(required)*_ - ID of the VFS product ("ID" or "Custom")<br>
* **template**:  - custom **PUBLIC** template url

##### Product ID
The Product ID method when invoking a product from the library

```json
"product": {
  "id": "16568",
}
```

##### Custom
The Custom method when invoking a product that is _*not*_ from the library

```json
"product": {
  "id": "custom",
  "template: "http://url_public_template.html"
}
```

!!! note
    The url must be publicly accessible.

#### Contact
_*(required)*_ - This is an array of recipients (contacts).   All the fields in the contact array are provided by you, the sponsor.  They are used in token replacement and for reference in the VFS system.

* **appuniqueid**:  *(required)* - a reference id of the sponsor contact.  *provided by you*
* **name**:  *(required)* - a reference 'name' of the sponsor contact.  *provided by you*
* **email**:  *(required)* - the recipients email address. *provided by you*
* **callbackurl**:  This is where the email [events](https://readme.velma.io/#e8165fa0-c5ef-4d8a-ad70-254e61a22649) gets posted back to.  The sponsor, if they want to receive these events, will construct the url so they know which contact is working with the email.

```json
    "contact": [
            {
                "appuniqueid": "abcd1",
                "name": "Mary Contact",
                "callbackurl": "https://cbapi/c?id=abc123",
                "firstname": "Mary",
                "lastname": "Contact",
                "email": "mary.contact@gmail.com"
            },
            {
                "appuniqueid": "abcd2",
                "name": "Debbie Contact",
                "callbackurl": "https://cbapi/c?id=abcd2",
                "firstname": "Debbie",
                "lastname": "Contact",
                "email": "deb.contact@gmail.com"
            },
            {
                "appuniqueid": "abcd3",
                "name": "Robert Contact",
          "callbackUrl": "https://cbapi/contact?id=abcd3",
                "firstname": "Robert",
                "lastname": "Contact",
                "email": "rob.contact@gmail.com"
            }
    ]
```


#### Sample Command Packet

```json
{
   "version": "1.6",
   "type": "email",
   "authentication": {
       "sponsorkey": "0a3c5aad8cfb496eae7966339a024965",
       "clientkey": "DEMO6661549e4aa9811754bb29880cc9"
   },
   "email": {
       "subject": "Demo Email",
       "from" : {
           "name": "John Public",
           "email": "john.public@1stdemomortgage.com"
       }
   },
   "user": {
        "appuniqueid": "1234",
        "fullname": "John Public",
        "title": "Loan Officer",
        "email": "john.public@velma.com",
        "company": "1ST DEMO",
        "citystatezip": "x El Segundo, CA 90245 x",
        "cellphone":"(208) 555-6969",
        "officephone": "(208) 555-9696",
        "photo": "https://as.velma.com/user/6560/settings/PersonalPhoto.jpg",
        "logo": "https://as.velma.com/user/6560/settings/BusinessLogo.jpg",
        "website": "https://readme.velma.io/",
        "disclaimer": "1ST DEMO Disclaimer"
   },  
   "product": {
        "id": "197"
   },
   "contact": [
       {
        "appuniqueid": "9876",
            "callbackUrl": "https://api.vfs.velma.com/test/capture/json",
            "name": "Mary Public",
            "firstname": "Mary",
            "lastname": "Public",
            "email": "contactemail@gmail.com"
       }
   ]
}
```
