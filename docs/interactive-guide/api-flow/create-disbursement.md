## Create a Payment

There are following payment methods for disbursments

 1. Debit
 2. ACH
 3. PayPal
 4. Venmo
 5. Money Network
 6. ECHEK
 7. Coinbase

### Debit - Description
This request is the payment call where we will take our `enrolment_vault` token and use it to create a disbursement payment for a recipient. The key variables here are `merchantTransactionId`, this must be unique for every transaction call , as well as paymentType which should correspond to the payment type associated with your environment for eg. Gaming, Claims, Wages etc. The EV token will never expire for the same `merchantCustomerId` and we can perform many number of transactions using same EV token.

[![Try it out](../../../../assets/images/button.png)](../api/?type=post&path=/ddp/v1/recipients)


### ACH - Description

An ACH is an electronic fund transfer made between banks and credit unions across what is called the Automated Clearing House network. This is an ACH payment request  where we will take our `enrolment_vault`token and use it to create a disbursement payment for a recipient. The key variables here are `merchantTransactionId`, this must be unique for every transaction call , as well as paymentType which should correspond to the payment type associated with your environment.

[![Try it out](../../../../assets/images/button.png)](../api/?type=post&path=/ddp/v1/recipients)


### PayPal - Description

This request is the payment call using the PayPal payment method, where we can use the `email` or `phoneNumber`  variables to initate the payments. The key variables here are `merchantTransactionId`, this must be unique for every transaction call , as well as paymentType which should correspond to the payment type associated with your environment.

[![Try it out](../../../../assets/images/button.png)](../api/?type=post&path=/ddp/v1/recipients)


## Venmo - Description

This request is the payment call using the Venmo payment method, where we can use the `email` or `phoneNumber`  variables to initate the payments. The key variables here are `merchantTransactionId`, this must be unique for every transaction call , as well as paymentType which should correspond to the payment type associated with your environment.

[![Try it out](../../../../assets/images/button.png)](../api/?type=post&path=/ddp/v1/recipients)


## Money Network - Description

This request is the payment call using the Money Network payment method, where we will take our `enrolment_vault` token and use it to create a disbursement payment for a recipient. The key variables here are `merchantTransactionId`, this must be unique for every transaction call , as well as paymentType which should correspond to the payment type associated with your environment for eg. Gaming, Claims, Wages etc. The EV token will never expire for the same `merchantCustomerId` and we can perform many number of transactions using same EV token.

[![Try it out](../../../../assets/images/button.png)](../api/?type=post&path=/ddp/v1/recipients)


## ECHECK- Description

This request is the payment call using the E-Check payment method to create a disbursement payment for a recipient. The key variables here are `merchantTransactionId`, this must be unique for every transaction call , as well as paymentType which should correspond to the payment type associated with your environment for eg. Gaming, Claims, Wages etc. 

[![Try it out](../../../../assets/images/button.png)](../api/?type=post&path=/ddp/v1/recipients)



## Coinbase- Description

This request is the payment call using the Coinbase payment method to create a disbursement payment for a recipient. The key variables here are `merchantTransactionId`, this must be unique for every transaction call , as well as paymentType which should correspond to the payment type associated with your environment for eg. Gaming, Claims, Wages etc. The EV token will never expire for the same `merchantCustomerId` and we can perform many number of transactions using same EV token.

[![Try it out](../../../../assets/images/button.png)](../api/?type=post&path=/ddp/v1/recipients)
