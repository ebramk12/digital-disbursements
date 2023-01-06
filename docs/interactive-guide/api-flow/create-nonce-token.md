## Step 3: Create the Account Nonce Token 
### Description
In this request you will utilize the publicKey returned in step 4 to encrypt your PCI data. Once that is done you will pass that data into this call and receive a nonce token to be used in the upcoming step. Keep in mind the encrypted payload for each variable should be surrounded by “ENC[]” as shown in the examples.
### **Header Change**
For just this call the header will be slightly modified as below:
Authorization: Bearer “tokenId” (generated from Step 2, example below)
Bearer AGG596cV67WF8DjYLE3kS6nSu36x
### Endpoint URL
Method: POST
URL: https://int.api.firstdata.com/ucom/v1/account-tokens
### Sample Request (Debit w/ Minimal Info)
### Sample Request(ACH w/ Minimal Info)