# Step 3: Create the Account Nonce Token

### Description
In this request you will utilize the publicKey returned in step 4 to encrypt your PCI data. Once that is done you will pass that data into this call and receive a nonce token to be used in the upcoming step. Keep in mind the encrypted payload for each variable should be surrounded by `ENC[ ]` as shown in the examples.

<!-- theme: failure -->
>### **Header Change**
>| Header Key | Change |
>| ---------- | ------ |
>| **Authorization** |  changes to `Bearer <tokenId>` (generated from Step 2, example below) |
>
><!-- theme: success-->
>> *Example `Autorization: Bearer AGG596cV67WF8DjYLE3kS6nSu36x`*

[![See Examples](../../../../assets/images/button.png)](/product/UniversalCommerce/api/?type=get&path=/v1/account-tokens/{nonceTokenId}&branch=develop&version=1.0.0)