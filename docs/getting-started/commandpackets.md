
Command Packets are at the core of all jobs in Velma.io.

They contain all of the data and instructions that  Velma.io needs to provide intelligent communication.

### Nodes

1. Type - Tells Velma.io what type of job we are sending it.
2. Authentication - Who is sending it.
3. Product - Which product it is going to work with.
4. Email - The source of the communication. (Print, SMS, Etc)
5. User - The senders data. (Also referred to as user tokens)
6. Contact - The recipients data.  (Also referred to as contact tokens)
7. Template - Document specific data

#### Sample Email Command Packet

```json
{
    "version": "1.7",
    "type": "email",
    "authentication": {
	    "sponsorkey": "1234"
	    "clientkey": "abcd"
	},
	"email": {
		"subject": "My subject Line"
		"from": {
			"name": "John Public"
			"email": "jobhnpublic@velma.io"
    },
    "product": "
	    "id": "123"
	",
	"template": {
		"loanAmount": "250000",
		"loanInterestRate": "5.8%",
		"loanDownPayment": 20000"
	}.
    "user": {
        "zip": "83686",
        "firstName": "John",
        "lastName": "Public",
        "fullName": "John Public",
        "address2": "Suite 200",
        "city": "Nampa"
    },
    contact": [
	  {
	     "appuniqueid": "abc"
         "firstname": "Nate"
         "lastname": "Public"
         "name": "Nate Public"
         "phone": "555-1234"
      },
      {
	     "appuniqueid": "def"
         "firstname": "Greg"
         "lastname": "Public"
         "name": "Greg Public"
         "phone": "555-1235"
      },
      {
	     "appuniqueid": "ghi"
         "firstname": "Dave"
         "lastname": "Public"
         "name": "Dave Public"
         "phone": "555-1236"
      }  
    ]      
}
```


### Products

Products are the communication assets in Velma.io.

They are HTML and/or text which, when invoked by a command packet, can intelligently transform themselves into a robust communication message tailored for each senders targeted recipient(s).

<small>Simple Happy Birthday Email</small>

![enter image description here](https://s3-us-west-2.amazonaws.com/vfs-docs/APIDocs/Simple+-+Email+Workflow/SimpleEmail.jpg)


### Command Packet & Products

The command packet data and the product tokens are used in two ways:

1. Tokens are replaced by the data in the command packet.
2. The data is used to dynamically transform the product.

#### Simple Tokens
```
{{user.fullname}}
{{user.title}}
```

#### Smart Tokens
These are tokens that show based on the existence of a value.

```html
<div vf-show="user.fullname">
	Hi <span vf-var="user.fullname">John Smith</span>
</div>
```

!!! note
    What this means is that you must construct the product to facilitate your custom communication.


##### Use Cases
There are really two distinct types of use cases.

###### One-to-One Communication (Transactional)

The setup of the product is designed to target its contact or contacts based solely on the data outside the contact node.

!!! tldr "Explained"
    Say you are sending loan information from John to Nate . In this case your desired communication product will need to be built based on the data in the **user** _and_ **template** nodes..


####### Sample

```html
Your new house <img src="{{user.housePic}}".

Hi, this is {{user.firstName}}, I just wanted to tell you the exciting news that your
loan amount of {{template.loanAmount}} with a down payment of {{template.loanDownPayment}}
is currently in the status of {{template.loanStatus}}.

Sincerely,
{{user.fullName}}
{{user.company}}
{{user.companyPositive}}
```

This would render as:

```html
Pretty House Picture here.

Hi, this is John, I just wanted to tell you the exciting news that your
loan amount of $250,000 with a down payment of $20,000
is currently in the status of Final Processing.

Sincerely,
John Public
XYZ Mortgage
Making your dreams a reality
```

!!! note ""
    The important thing to note here is that even though in the command packet there are two contacts, the messaging is designed around the information related to contact one (Nate) and the second contact (Greg) is really just CC'd communication.


```json
{
    "<Other Nodes>",
    "user": {
        "zip": "83686",
        "firstName": "John",
        "lastName": "Public",
        "fullName": "John Public",
        "company": "xyx Mortgage",
        "companyPositive": "Making your dreams a reality",
        "address2": "Suite 200",
        "city": "Nampa",
        "housePic": "https://userdata.prettypic.jpg"
    },
    "template": {
		"loanAmount": "250000",
		"loanInterestRate": "5.8%",
		"loanDownPayment": 20000",
		"loanStatus": "finalProcessing"
	}.
    contact": [
	  {
	     "appuniqueid": "abc"
         "firstname": "Nate"
         "lastname": "Borrower"
         "name": "Nate Public"
         "phone": "555-1234",
         "email": nate@gmail.com"
      },
      {
	     "appuniqueid": "def"
         "firstname": "Greg"
         "lastname": "Co-Borrower"
         "name": "Greg Co-Borrower"
         "phone": "555-1234",
         "email": "greg@gmail.com"
      }

    ]      
}
```

###### One to many (Marketing)

The setup of the product is designed to target many contacts.

!!! tldr "Explained"
    Say you are sending an information  type marketing email to many contacts. In this case your desired communication product will need to be built based on the data in the contact node.

***Example Messaging***

&nbsp;
&nbsp;  

```
House <img src="{{user.housePic}}".

Hi {{contact.firstName}}, this is {{user.firstName}}, I just wanted to let you know that a new residence has become available, it is in a nice suburban area of town. View the details here {{user.houseDetails}}   

Yours Truly {{user.fullName}}
{{user.company}}
{{user.companyPositive}}
```
&nbsp;
&nbsp;  

This would translate to 3 emails

&nbsp;
&nbsp;  
```
House "House Picture here"

Hi Nate or Nate or Greg, this is John, I just wanted to let you know that a new residence has become available, it is in a nice suburban area of town. View the details here https://userdata.housedetails.html   

Yours Truly John Public
XYZ Mortgage
Making your dreams a reality
```
&nbsp;
&nbsp;  

**The imporant thing to note is that the messaging is targeting all three contacts>**


```json
{
    "<Other Nodes>",
    "user": {
        "zip": "83686",
        "firstName": "John",
        "lastName": "Public",
        "fullName": "John Public",
        "company": "xyx Mortgage",
        "companyPositive": "Making your dreams a reality",
        "address2": "Suite 200",
        "city": "Nampa",
        "houseDetails": "https://userdata.housedetails.html".
        "housePic": "https://userdata.prettypic.jpg"
    },
    contact": [
	  {
	     "appuniqueid": "abc"
         "firstname": "Nate"
         "lastname": "Borrower"
         "name": "Nate Borrower"
         "phone": "555-1234",
         "email": nate@gmail.com"
         "template": {
				"loanAmount": "250001",
				"loanInterestRate": "5.1%",
				"loanDownPayment": 20001",
				"loanStatus": "finalProcessing"
		 }.
      },
      {
	     "appuniqueid": "def"
         "firstname": "Greg"
         "lastname": "Public"
         "name": "Borrower"
         "phone": "555-1235",
         "email": "greg@gmail.com"
         "template": {
				"loanAmount": "250002",
				"loanInterestRate": "5.2%",
				"loanDownPayment": 20002",
				"loanStatus": "finalProcessing"
		 }
      },
      {
	     "appuniqueid": "def"
         "firstname": "Dave"
         "lastname": "Borrower"
         "name": "Dave Borrower"
         "phone": "555-1236",
         "email": "dave@gmail.com",
         "template": {
				"loanAmount": "250003",
				"loanInterestRate": "5.3%",
				"loanDownPayment": 20003",
				"loanStatus": "finalProcessing"
		 }
      }
    ]      
}
```
