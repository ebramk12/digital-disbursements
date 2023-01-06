## Step 4: Vault a Payment Method
### Description
This request will take our generated nonce from Step 3 in the payload as well as the tokenId from Step 2 in the headers. Once this step is completed the payment method will be vaulted and an EV (Enrolment Vault) token will be generated. These tokens are specific to payment methods vaulted with Fiserv and are not to be confused with TA (TransArmor) tokens which are generated through other flows.
### **Header Change**
For just this call the header will contain an additional field, with authorization going back to the normal HMAC signature.
Add: access_token: “tokenId” (the same tokenId used in the Bearer authorization in step 3)
Example: access_token: AGG596cV67WF8DjYLE3kS6nSu36x
### Endpoint URL
Method: POST
URL: https://int.api.firstdata.com/ddp/v1/recipients/{{merchantCustomerId}}/accounts
### Sample Request