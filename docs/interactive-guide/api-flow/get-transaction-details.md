## Get (Retrieve) Status for the following services

1. Get Recipient Info
2. Get Recipent Accounts
3. Get Transaction Status
4. Get Merchant Info

## Get Recipient Info 

### Description
This request will retrieve the information for a recipient based upon its valid `merchantCustomerId` passed in the URL. With this retrieve call you can get the detailed information of the previously created recipient. 


[![Try it out](../../../../assets/images/button.png)](../api/?type=post&path=/ddp/v1/recipients)


## Get Recipient Accounts 

### Description
This request will retrieve the account information based on the recipientId. This will return ALL associated payment methods with this `recipientId`. Remember the `recipientId` changes based upon email so if multiple merchantCustomerIds share the same email this will pull all the accounts from every merchantCustomerId associated with that email. 


[![Try it out](../../../../assets/images/button.png)](../api/?type=post&path=/ddp/v1/recipients)


## Get Transaction Status

### Description
This request will get the details of a transaction and will take either `merchantCustomerId` or 'merchantTransactionId' in the request parameter. The prerequisite is to have a transaction initiated or disbursed using the payment API. Please refer transaction initiate/disburse section in the following link for more information. 

Using `merchantCustomerId`: This request can be used when you want to view all the transactions for that merchant customer id  

[![Try it out](../../../../assets/images/button.png)](../api/?type=post&path=/ddp/v1/recipients)

Using `merchantTransactionId`: This request to be used when you want to view the details of a particular transactions 

[![Try it out](../../../../assets/images/button.png)](../api/?type=post&path=/ddp/v1/recipients)



## Get Merchant Info

### Description
This request will get the details of the onboarded merchant with no request parameter only the headers are required. With this call you can get the full information of the merchant like ledger balance, Available balance, DFA Account Number, Merchant Name & Address details etc.


[![Try it out](../../../../assets/images/button.png)](../api/?type=post&path=/ddp/v1/recipients)
