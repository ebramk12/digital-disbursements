# Step 3: Create the Account Nonce Token

### Description
In this request you are going to encrypt your PCI (Payment Card Industry) data with the help of Public Key and TokenId generated in "Create a Public Token" API call in previous step. Once that is done you will pass that data into this call and receive a nonce token to be used in the upcoming step for account vaulting. Keep in mind the encrypted payload for each variable should be surrounded by `ENC[ ]` as shown in the examples.

<!-- theme: failure -->
>### **Header Change**
>| Header Key | Change |
>| ---------- | ------ |
>| **Authorization** |  changes to `Bearer <tokenId>` (generated from Step 2, example below) |
>
><!-- theme: success-->
>> *Example `Autorization: Bearer AGG596cV67WF8DjYLE3kS6nSu36x`*

[![See Examples](../../../../assets/images/button.png)](/product/UniversalCommerce/api/?type=get&path=/v1/account-tokens&branch=develop&version=1.0.0)


[UCOM Account Service](/product/UniversalCommerce/api/?type=get&path=/v1/account-tokens&branch=develop&version=1.0.0)