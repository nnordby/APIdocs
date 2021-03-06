`:::js GET` Get single product.

`https://api.vfs.velma.com/v1-product/products/:productId`

##### Params <small>_(Path Variables)_</small>

| KEY    |  VALUE    |
|--------|-----------|
| productId|  202 |

#### Headers

| KEY    |  VALUE    |   DESCRIPTION      |
|--------|-----------|--------------------|
| Authorization|  jwt {{Token}}| <small>generated by Velma</small |
| x-api-key | 49ep6U3OEH2UR56Dg4BNp6qKxNCnKeDP3l29cyZg | <small>provided following on-boarding |
| Content-Type | application/json |  |


##### Example Request
`:::js Get Products`

```bash tab="Curl"
curl --location --request GET "https://api.vfs.velma.com/v1-product/products/202" \
  --header "Authorization: jwt eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ2ZXIiOiIxLjAiLCJhcGlLZXkiOiI0OWVwNlUzT0VIMlVSNTZEZzRCTnA2cUt4TkNuS2VEUDNsMjljeVpnIiwic3BvbnNvcktleSI6IjBhM2M1YWFkOGNmYjQ5NmVhZTc5NjYzMzlhMDI0OTY1IiwiaXNzIjoiRE1PIiwiY2xpZW50S2V5IjoiREVNTzY2NjE1NDllNGFhOTgxMTc1NGJiMjk4ODBjYzkiLCJ1c2VyTmFtZSI6IkRFTU9VU0VSIiwidXNlcklkIjoiREVNTzEyMzQ1NjU0MzIxIiwiZnVsbE5hbWUiOiJERU1PIFVTRVIiLCJlbWFpbCI6ImRlbW91c2VyQG1haWxpbmF0b3IuY29tIiwiaWF0IjoxNTQxMDg3NjA1LCJleHAiOjE1NDEwOTEyMDUsInJvbGVzIjpbIkxJQjo0MCIsIkFDVDoxMCIsIkpPQjoxMCJdLCJqdGkiOiJmZTlkNGRlNC0yODkzLTQ0OGEtYmNkNy1kNjU4OTcwNWMwNjQifQ.6GThUc3s_xLOG2dkPx8Add3g4nF3VqSSAAH-g9bpQbc" \
  --header "x-api-key: 49ep6U3OEH2UR56Dg4BNp6qKxNCnKeDP3l29cyZg" \
  --header "Content-Type: application/json"
```

```js tab="Node"
var https = require('https');

var options = {
  'method': 'GET',
  'hostname': 'https://api.vfs.velma.com',
  'path': '/v1-product/products/202',
  'headers': {
    'Authorization': 'jwt eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ2ZXIiOiIxLjAiLCJhcGlLZXkiOiI0OWVwNlUzT0VIMlVSNTZEZzRCTnA2cUt4TkNuS2VEUDNsMjljeVpnIiwic3BvbnNvcktleSI6IjBhM2M1YWFkOGNmYjQ5NmVhZTc5NjYzMzlhMDI0OTY1IiwiaXNzIjoiRE1PIiwiY2xpZW50S2V5IjoiREVNTzY2NjE1NDllNGFhOTgxMTc1NGJiMjk4ODBjYzkiLCJ1c2VyTmFtZSI6IkRFTU9VU0VSIiwidXNlcklkIjoiREVNTzEyMzQ1NjU0MzIxIiwiZnVsbE5hbWUiOiJERU1PIFVTRVIiLCJlbWFpbCI6ImRlbW91c2VyQG1haWxpbmF0b3IuY29tIiwiaWF0IjoxNTQxMDg3NjA1LCJleHAiOjE1NDEwOTEyMDUsInJvbGVzIjpbIkxJQjo0MCIsIkFDVDoxMCIsIkpPQjoxMCJdLCJqdGkiOiJmZTlkNGRlNC0yODkzLTQ0OGEtYmNkNy1kNjU4OTcwNWMwNjQifQ.6GThUc3s_xLOG2dkPx8Add3g4nF3VqSSAAH-g9bpQbc',
    'x-api-key': '49ep6U3OEH2UR56Dg4BNp6qKxNCnKeDP3l29cyZg',
    'Content-Type': 'application/json'
  }
};

var req = https.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });

  res.on("error", function (error) {
    console.error(error);
  });
});

req.end();
```

```js tab="JQuery"
var settings = {
  "url": "https://api.vfs.velma.com/v1-product/products/202",
  "method": "GET",
  "timeout": 0,
  "headers": {
    "Authorization": "jwt eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ2ZXIiOiIxLjAiLCJhcGlLZXkiOiI0OWVwNlUzT0VIMlVSNTZEZzRCTnA2cUt4TkNuS2VEUDNsMjljeVpnIiwic3BvbnNvcktleSI6IjBhM2M1YWFkOGNmYjQ5NmVhZTc5NjYzMzlhMDI0OTY1IiwiaXNzIjoiRE1PIiwiY2xpZW50S2V5IjoiREVNTzY2NjE1NDllNGFhOTgxMTc1NGJiMjk4ODBjYzkiLCJ1c2VyTmFtZSI6IkRFTU9VU0VSIiwidXNlcklkIjoiREVNTzEyMzQ1NjU0MzIxIiwiZnVsbE5hbWUiOiJERU1PIFVTRVIiLCJlbWFpbCI6ImRlbW91c2VyQG1haWxpbmF0b3IuY29tIiwiaWF0IjoxNTQxMDg3NjA1LCJleHAiOjE1NDEwOTEyMDUsInJvbGVzIjpbIkxJQjo0MCIsIkFDVDoxMCIsIkpPQjoxMCJdLCJqdGkiOiJmZTlkNGRlNC0yODkzLTQ0OGEtYmNkNy1kNjU4OTcwNWMwNjQifQ.6GThUc3s_xLOG2dkPx8Add3g4nF3VqSSAAH-g9bpQbc",
    "x-api-key": "49ep6U3OEH2UR56Dg4BNp6qKxNCnKeDP3l29cyZg",
    "Content-Type": "application/json"
  },
};
$.ajax(settings).done(function (response) {
  console.log(response);
});
```

##### Example Response
`:::js 200 OK`

```bash
{
  "id": "202",
  "name": "Word of Mouth is Priceless",
  "description": "Thank you for doing business with us. We hope you valued our services...",
  "mediaType": "email",
  "classification": "Marketing",
  "tags": "",
  "isActive": true,
  "thumbUrl": "https://vfs-library.s3.amazonaws.com/prod/202/template.thumb?versionId=7DvDw81uk7oR4ZLg8MQcv8oTUKFwOxVj",
  "previewUrl": "https://vfs-library.s3.amazonaws.com/prod/202/template.preview.1?versionId=LD23RwGqaJ0lUU.swAJSlzPcuVgG2vNr",
  "sponsorId": "213ab0c746f84ef6b412234992576f53",
  "createDate": "2018-03-22T21:50:34.805Z",
  "updateDate": "2018-10-21T16:51:44.920Z",
  "pricing": {
    "priceId": "temp_price_entry",
    "perUnitPostage": 0,
    "perUnitPrice": 0,
    "priceName": "TEMP PRICE",
    "source": "product"
  },
  "missingAttributes": [],
  "attributes": [
    {
      "key": "template.url",
      "url": "https://vfs-library.s3.amazonaws.com/prod/202/template.url",
      "contentType": "text/html",
      "attributeType": "html",
      "canRemove": true,
      "canUpdate": true
    }
  ]
}
```
