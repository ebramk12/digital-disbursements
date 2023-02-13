# Step 2: Create a Public Token

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
[![Try it out](../../../../assets/images/button.png)](../api/?type=post&path=/ucom/v1/tokens)