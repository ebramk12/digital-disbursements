## Save a Payment Method

### Description

There are following steps require to save (vault) a payment methond for the recipient.

 1. Create a Public Token
 2. Create the Account Nonce Token
 3. Vault the paymment method


# Create a Public Token

## Description
This request will generate a public key to be used in encrypting PCI data as well as a `tokenId` to be passed to subsequent calls through the header. This `tokenId` and the `publicKey` is valid for 20 minutes and after than its expired, you will use the public Key to perform encryption  on the account details as follow:

| Account Type | Items to Encrypt             |
| ------------ | ---------------------------- |
| Debit        | Card Number, Month, and Date |
| ACH          | Acount Number                |

<!-- theme: success -->
>### Special considerations
>| Parameter               | Note                                                                                                                                                                                   |
>| ----------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | 
>| **fdCustomerId**       | How the customer is identified in the ucom app. Best practice would be to use the same value as `merchantCustomerId`.                                                                 |


<!-- TODO: Needs correct link to Get Encryption Key API -->
[![Try it out](../../../../assets/images/button.png)](../api/?type=post&path=/ddp/v1/recipients)



# Create the Account Nonce Token

<!--
type: tab
titles: API, Hosted 
-->

### Description
In this request you are going to encrypt your PCI (Payment Card Industry) data with the help of `publicKey` and `tokenId` generated in "Create a Public Token" API call in previous step. Once that is done you will pass that data into this call and receive a nonce token to be used in the upcoming step for account vaulting. Keep in mind the encrypted payload for each variable should be surrounded by `ENC[ ]` as shown in the examples.

<!-- theme: failure -->
>### **Header Change**
>| Header Key | Change |
>| ---------- | ------ |
>| **Authorization** |  changes to `Bearer <tokenId>` (generated from Step 1, example below) |
>
><!-- theme: success-->
>> *Example `Autorization: Bearer AGG596cV67WF8DjYLE3kS6nSu36x`*

[![See Examples](../../../../assets/images/button.png)](/product/UniversalCommerce/api/?type=get&path=/v1/account-tokens/{nonceTokenId}&branch=develop&version=1.0.0)


[UCOM Account Service](/product/UniversalCommerce/api/?type=get&path=/v1/account-tokens/{nonceTokenId}&branch=develop&version=1.0.0)

<!--
type: tab
-->

### Description

HPP is a web SDK and iFrame solution. DDP is intended to provide merchants with an option to capture the cardholder data in secure manner through HPP. Secure card capture is to allow merchants to embed the HP SDK into their existing website/web view. This SDK solution offered by DDP platform shall load in iFrame and comply the PCI requirements. In addition to the core functionality of HPP, It shall provide a capability to customize the UI to match the merchant's website style.

[![Guide](../../../../assets/uCom_HostedPages2_Integration_Guide.pdf)]

<!-- type: tab-end -->

---

# Vault a Payment Method

### Description

This request will take our generated nonce token from previous step in the payload as well as the `tokenId` from Step 1 in the headers. Once this step is completed the payment method will be vaulted and an EV (Enrolment Vault) token will be generated. These tokens are specific to payment methods vaulted with Fiserv and are not to be confused with TA (TransArmor) tokens which are generated through other flows. This EV token can be non-expired tokens and can be used multiple times for that recipeient.

<!-- theme: failure -->
>### **Header Change**
>| Header Key | Change |
>| ---------- | ------ |
>| Authorization | returns to normal HMAC signature |
>| access_token  | the same `tokenId` used in the Bearer authorization in step 3 (*ex.* `access_token: AGG596cV67WF8DjYLE3kS6nSu36x`) |
><!-- TODO: ADD EXAMPLES HERE-->

[![Try it out](../../../../assets/images/button.png)](../api/?type=post&path=/ddp/v1/recipients)