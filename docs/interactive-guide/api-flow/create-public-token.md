# Step 2: Create a Public Token

## Description
This request will generate a public key to be used in encrypting PCI data as well as a `tokenId` to be passed to subsequent calls through the header. 

<!-- Theme: Success -->
>### Special considerations
>| Parameter               | Note                                                                                                                                                                                   |
>| ----------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | 
>| **fdCustomerId**        | How the customer is identified in the ucom app. \nBest practice would be to use the same value as merchantCustomerId.                                                                 |

<!-- TODO: Needs correct link to Get Encryption Key API -->
[![Try it out](../../../../assets/images/button.png)](../api/?type=post&path=/ddp/v1/recipients)