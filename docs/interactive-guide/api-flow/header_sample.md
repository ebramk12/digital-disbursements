# Sample Headers
## Header Descriptions
The header of Each API call will contain several parameters. It is important that each parameter contain the specified values to have a successful API Call. Any changes to the values will be noted through out the guide.

<!-- theme: success -->
>| Key               | value            |
>| ----------------- | ---------------- |
>| Content-Type      | application/json |
>| Client-Request-Id | "Any unique ID, usually a guid. Must be unique per each request" |
>| Api-Key           | "Your Sandbox KEY goes here" |
>| Authorization     | HMAC "Encrypted payload as signature here, shown below" |
>| Timestamp         | "Current time in EPOCH notation" |

## Example
```
Content-Type:application/json
Client-Request-Id:4da61bfb-6852-4f2a-9462-733276f633d7
Api-Key: YMgw8VSrYMG6WTIUnoUUGv7hF9Aqh3EO
Authorization:HMAC W5X9NAlPgSNsfQX55fXbXrk3arzL6KxcCTA6SrnxL+U=
Timestamp: 1607368688646
```

## How to generate HMAC Signature

### Description
HMAC signature is used in all calls made to our API and is necessary to receive a successful response from the system.

### High Level Flow
- Get and save the current time
- Identify and save the request method
- Take the environment key and append a colon along with the current time
- Save this as the current raw signature (key:time)
- Get and save the payload from the request
- If the request method is not POST, move directly to step 7.
- Encrypt the request payload using SHA256 and save it
- Take this encrypted payload, make it a string and then encrypt it using Base64.
- Take the raw signature from step 4, append a colon and the Base64 encrypted payload to it and save it.
- Take the raw signature and HMAC encrypt it using SHA256 against the environment secret.
- Finally taake this encrypted raw signature, make it a string and then encrypt it using Base64 to produce the signature for the header.

### Postman Example
```
var key = postman.getEnvironmentVariable('clientKey');
var secret = postman.getEnvironmentVariable('clientSecret');
var time = new Date().getTime();
var method = request.method;
var rawSignature = key + ":" + time;
var requestBody = request.data;
if (method != 'GET' && method != 'DELETE') {
var payload_digest = CryptoJS.SHA256(requestBody);
var b64BodyContent = CryptoJS.enc.Base64.stringify(payload_digest);
rawSignature = rawSignature + ":" + b64BodyContent;
}
var signature = CryptoJS.HmacSHA256(rawSignature, secret);
postman.setEnvironmentVariable('time', time);
postman.setEnvironmentVariable('signature', CryptoJS.enc.Base64.stringify(signature));
```