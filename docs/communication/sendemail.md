The email workflow is  a simple way to POST a small piece of JSON to velma.io and have it send a fully tokenized and rendered email to your recipients.   

**Steps:**

1. **Choose or create a Product**

2. **Create Command Packet**

3. **Post Command Packet**

#### Step 1. Choose (or create) a Product


Choose or edit an existing product or create your own
!!! example
    See the <img src="/images/postmanIcon.png" width="24" align="left" style="padding-right: 5px;"><a href="https://readme.velma.io/#13223d0c-c9fa-44cf-b8f0-1de9d562a030" target="_blank">Get Products</a> Postman Collection.

Here we have created a simple Happy Birthday email in the online Velma.io Product creator.

---
![enter image description here](https://s3-us-west-2.amazonaws.com/vfs-docs/APIDocs/Simple+-+Email+Workflow/SimpleEmail.jpg)


The product ID in this case is **200** so if you look at the Command Packet (JSON) being posted you will see the product node has an id of "200".

There are two ways of [configuring the product node][2] in Velma.io for a simple email.

1. Use an existing product id
2. Use a custom URL.

[2]: /getting-started/commandpacket-spec/#product

Using an existing product.

```json
"product": {
	"id": "200" -- if you are using a velma.io product
}
```
Using a custom url.

```json
"product": {
	"id": "CUSTOM", -- tells Velma.io that a custom url is to be used
	"url: "<custom public url>" -- NOTE: this must be a publicly accessible URL.
}
```


Here is a sample command packet below:


Inside the html of the product there are tokens such as:

*General Tokens*

```html
{{user.fullname}}
{{user.title}}
```

*Smart Tokens*
- these are tokens that show based on the existence of a value.

```html
<div vf-show="user.fullname">
	Hi <span vf-var="user.fullname">John Smith</span>
</div>
```


#### Step 2. Create Command Packet

Velma.io will replace those tokens with the values in the command packet and email the document to the email in the contact node.


Command Packet:

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
        "id": "200"
   },
   "contact": [
       {
        "appuniqueid": "9876",
            "callbackUrl": "https://api.vfs.velma.com/dev/capture/json",
            "name": "Mary Public",
            "firstname": "Mary",
            "lastname": "Public",
            "email": "{{contact-email}}"
       }
   ]
}
```

#### Step 3. Post Command Packet

All that is required is posting the command packet to the endpoint.

`https://api.vfs.velma.com/v1/job`


##### Sample Curl Request

```bash
curl -X POST \
  https://api.vfs.velma.com/v1/job \
  -H 'Content-Type: application/json' \
  -H 'Postman-Token: e9563fab-b3bb-4527-8660-ddec304120ee' \
  -H 'cache-control: no-cache' \
  -H 'x-api-key: 49ep6U3OEH2UR56Dg4BNp6qKxNCnKeDP3l29cyZg' \
  -d '{
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
        "id": "200"
   },
   "contact": [
       {
        "appuniqueid": "9876",
            "callbackUrl": "https://api.vfs.velma.com/dev/capture/json",
            "name": "Mary Public",
            "firstname": "Mary",
            "lastname": "Public",
            "email": "velmaiois@mailinator.com"
       }
   ]
}'
```
