## Step 4: Vault a Payment Method

### Description
This request will take our generated nonce from Step 3 in the payload as well as the tokenId from Step 2 in the headers. Once this step is completed the payment method will be vaulted and an EV (Enrolment Vault) token will be generated. These tokens are specific to payment methods vaulted with Fiserv and are not to be confused with TA (TransArmor) tokens which are generated through other flows.

<!-- theme: failure -->
>### **Header Change**
>| Header Key | Change |
>| ---------- | ------ |
>| Authorization | returns to normal HMAC signature |
>| access_token  | the same `tokenId` used in the Bearer authorization in step 3 (*ex.* `access_token: AGG596cV67WF8DjYLE3kS6nSu36x`) |

