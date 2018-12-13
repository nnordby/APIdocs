You will use the keys provided to you during onboarding to generate a JWT token.
If running in Postman, the system will create a jwt-token property for you automatically in your enivronment.

##### Generate JWT Token

```bash tab="Curl"
curl --request POST \
  --url 'https://api.vfs.velma.com/v1-account/auth/token/generate' \
  --header 'Content-Type: application/json' \
  --header 'jwtPassword: 8cbbab28a62d42499c51be352a731b66' \
  --header 'jwtUsername: 94a0d2d41f30433aa89691b46e75d8f3' \
  --header 'x-api-key: 49ep6U3OEH2UR56Dg4BNp6qKxNCnKeDP3l29cyZg' \
  --data '{
    "claims": {
        "apiKey": "49ep6U3OEH2UR56Dg4BNp6qKxNCnKeDP3l29cyZg",
        "sponsorKey": "0a3c5aad8cfb496eae7966339a024965",
        "sponsorCode": "DMO",
        "clientKey": "DEMO6661549e4aa9811754bb29880cc9",
        "userName": "DEMOUSER",
        "userId": "DEMO12345654321",
        "fullName": "DEMO USER",
        "email": "demouser@mailinator.com"
    }
}'
```

```js tab="Node"
var http = require("http");

var options = {
  "method": "POST",
  "hostname": [
    "https://api.vfs.velma.com"
  ],
  "path": [
    "v1-account",
    "auth",
    "token",
    "generate"
  ],
  "headers": {
    "x-api-key": "49ep6U3OEH2UR56Dg4BNp6qKxNCnKeDP3l29cyZg",
    "Content-Type": "application/json",
    "jwtUsername": "94a0d2d41f30433aa89691b46e75d8f3",
    "jwtPassword": "8cbbab28a62d42499c51be352a731b66"
  }
};

var req = http.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function () {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });
});

req.write(JSON.stringify({ claims:
   { apiKey: '49ep6U3OEH2UR56Dg4BNp6qKxNCnKeDP3l29cyZg',
     sponsorKey: '0a3c5aad8cfb496eae7966339a024965',
     sponsorCode: 'DMO',
     clientKey: 'DEMO6661549e4aa9811754bb29880cc9',
     userName: 'DEMOUSER',
     userId: 'DEMO12345654321',
     fullName: 'DEMO USER',
     email: 'demouser@mailinator.com' } }));
req.end();fd
```

```js tab="JQuery"
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "https://api.vfs.velma.com/v1-account/auth/token/generate",
  "method": "POST",
  "headers": {
    "x-api-key": "49ep6U3OEH2UR56Dg4BNp6qKxNCnKeDP3l29cyZg",
    "Content-Type": "application/json",
    "jwtUsername": "94a0d2d41f30433aa89691b46e75d8f3",
    "jwtPassword": "8cbbab28a62d42499c51be352a731b66"
  },
  "processData": false,
  "data": "{\n    \"claims\": {\n        \"apiKey\": \"49ep6U3OEH2UR56Dg4BNp6qKxNCnKeDP3l29cyZg\",\n        \"sponsorKey\": \"0a3c5aad8cfb496eae7966339a024965\",\n        \"sponsorCode\": \"DMO\",\n        \"clientKey\": \"DEMO6661549e4aa9811754bb29880cc9\",\n        \"userName\": \"DEMOUSER\",\n        \"userId\": \"DEMO12345654321\",\n        \"fullName\": \"DEMO USER\",\n        \"email\": \"demouser@mailinator.com\"\n    }\n}"
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

#### Sample Response
```bash
{
  "statusCode": "200",
  "body": {
    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ2ZXIiOiIxLjAiLCJhcGlLZXkiOiI0OWVwNlUzT0VIMlVSNTZEZzRCTnA2cUt4TkNuS2VEUDNsMjljeVpnIiwic3BvbnNvcktleSI6IjBhM2M1YWFkOGNmYjQ5NmVhZTc5NjYzMzlhMDI0OTY1IiwiaXNzIjoiRE1PIiwiY2xpZW50S2V5IjoiREVNTzY2NjE1NDllNGFhOTgxMTc1NGJiMjk4ODBjYzkiLCJ1c2VyTmFtZSI6IkRFTU9VU0VSIiwidXNlcklkIjoiREVNTzEyMzQ1NjU0MzIxIiwiZnVsbE5hbWUiOiJERU1PIFVTRVIiLCJlbWFpbCI6ImRlbW91c2VyQG1haWxpbmF0b3IuY29tIiwiaWF0IjoxNTIxNzQwNTkzLCJleHAiOjE1MjE3NDQxOTMsInJvbGVzIjpbIkxJQjo0MCIsIkFDVDoxMCJdLCJqdGkiOiI5MTljMGMzMi1mZTUzLTRhYzQtYWZhMC1kMzEzOTU2ODQ2YjUifQ.cgm7ktaMo73fRNz7YFYxF0fWXmi-_cgLQJI3vfYeT8k"
  }
}
```

!!! tip
    Make note of the JWT token as it will be used in future calls


!!! warning
    The JWT Token will expire in 24 hours

##### Headers
| key | value | description |
|-----|-------|-------------|
| **x-api-key** | 49ep6U3OEH2UR56Dg4BNp6qKxNCnKeDP3l29cyZg | <small>provided following on-boarding<small>|
|**Content-Type** | application/json||
|**jwtUsername**  | 94a0d2d41f30433aa89691b46e75d8f3 | <small>provided following on-boarding<small> |
|**jwtPassword**  | 8cbbab28a62d42499c51be352a731b66 | <small>provided following on-boarding<small> |

##### Body

```bash


{
    "claims": {
        "apiKey": "49ep6U3OEH2UR56Dg4BNp6qKxNCnKeDP3l29cyZg",
        "sponsorKey": "0a3c5aad8cfb496eae7966339a024965",
        "sponsorCode": "DMO",
        "clientKey": "DEMO6661549e4aa9811754bb29880cc9",
        "userName": "DEMOUSER",
        "userId": "DEMO12345654321",
        "fullName": "DEMO USER",
        "email": "demouser@mailinator.com"
    }
}
```

!!! example "Try it"
    See the <img src="../../images/postmanIcon.png" width="24" align="left" style="padding-right: 5px;"><a href="https://readme.velma.io/#a6912ad6-5197-4ea6-b923-e7c5f9ffde5d" target="_blank">Generate JWT</a> Postman Collection.
