## Create a Payment

### Description

There are following different payment methods for the disbursments, there are detailed descriptions are provided below for each of the payment methnods.

 1. Debit
 2. ACH
 3. Coinbase
 4. Money Network
 5. PayPal
 6. Venmo
 7. E-CHEK
 8. TA Token

### Debit

This request is the payment call where we will take our `enrolment_vault` token and use it to create a disbursement payment for a recipient. The key variables here are `merchantTransactionId`, this must be unique for every transaction call , as well as paymentType which should correspond to the payment type associated with your environment for eg. Gaming, Claims, Wages etc. The EV token will never expire for the same `merchantCustomerId` and we can perform many number of transactions using same EV token.

[![Try it out](../../../../assets/images/button.png)](../api/?type=post&path=/ddp/v1/payments/{id}/disburse)


### ACH 

An ACH is an electronic fund transfer made between banks and credit unions across what is called the Automated Clearing House network. This is an ACH payment request  where we will take our `enrolment_vault`token and use it to create a disbursement payment for a recipient. The key variables here are `merchantTransactionId`, this must be unique for every transaction call , as well as paymentType which should correspond to the payment type associated with your environment.

[![Try it out](../../../../assets/images/button.png)](../api/?type=post&path=/ddp/v1/payments/{id}/disburse)


### Coinbase

This request is the payment call using the Coinbase payment method to create a disbursement payment for a recipient. The key variables here are `merchantTransactionId`, this must be unique for every transaction call , as well as paymentType which should correspond to the payment type associated with your environment for eg. Gaming, Claims, Wages etc. The EV token will never expire for the same `merchantCustomerId` and we can perform many number of transactions using same EV token.


[![Try it out](../../../../assets/images/button.png)](../api/?type=post&path=/ddp/v1/payments/{id}/disburse)


### Money Network 

This request is the payment call using the Money Network payment method, where we will take our `enrolment_vault` token and use it to create a disbursement payment for a recipient. The key variables here are `merchantTransactionId`, this must be unique for every transaction call , as well as paymentType which should correspond to the payment type associated with your environment for eg. Gaming, Claims, Wages etc. The EV token will never expire for the same `merchantCustomerId` and we can perform many number of transactions using same EV token.

[![Try it out](../../../../assets/images/button.png)](../api/?type=post&path=/ddp/v1/payments/{id}/disburse)


### PayPal 

This request is the payment call using the PayPal payment method, where we can use the `email` or `phoneNumber`  variables to initate the payments. The key variables here are `merchantTransactionId`, this must be unique for every transaction call , as well as paymentType which should correspond to the payment type associated with your environment.

[![Try it out](../../../../assets/images/button.png)](../api/?type=post&path=/ddp/v1/payments/{id}/disburse)


### Venmo 

This request is the payment call using the Venmo payment method, where we can use the `email` or `phoneNumber`  variables to initate the payments. The key variables here are `merchantTransactionId`, this must be unique for every transaction call , as well as paymentType which should correspond to the payment type associated with your environment.

[![Try it out](../../../../assets/images/button.png)](../api/?type=post&path=/ddp/v1/payments/{id}/disburse)


### E-CHECK

This request is the payment call using the E-Check payment method to create a disbursement payment for a recipient. The key variables here are `merchantTransactionId`, this must be unique for every transaction call , as well as paymentType which should correspond to the payment type associated with your environment for eg. Gaming, Claims, Wages etc. 

[![Try it out](../../../../assets/images/button.png)](../api/?type=post&path=/ddp/v1/payments/{id}/disburse)

## TA Token

This request is the payment call using the TA Token payment method to create a disbursement payment for a recipient. The key variables here are `merchantTransactionId`, this must be unique for every transaction call , as well as paymentType which should correspond to the payment type associated with your environment for eg. Gaming, Claims, Wages etc. 

[![Try it out](../../../../assets/images/button.png)](../api/?type=post&path=/ddp/v1/payments/{id}/disburse)

## Cancel a Payment

### Description
This feature is to cancel a payment transaction which is in progress or waiting for settlement. This is applicable for any ACH transaction which is waiting for settlement. The prerequisite is to have a transaction initiated or disbursed using the payment API. The parameter required is the transaction id or TID [this is the unique id generated by DDP and is mapped 1:1 against the merchant transaction id. 
 
[![Try it out](../../../../assets/images/button.png)](../api/?type=post&path=/ddp/v1/payments/{id}/cancel)


