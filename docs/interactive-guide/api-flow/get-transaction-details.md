## Step 5a: Get Transaction Details (Optional/Informative)
### Description
Retrieve the details of a transaction or group of transactions. Using the merchantTransactionId will return the information for that single transaction, while utilizing the merchantCustomerId will pull all the transactions from that customer.
### Endpoint URL
Method: GET
URL: https://int.api.firstdata.com/ddp/v1/transactions/{{merchantTransactionId}}
OR
URL: https://int.api.firstdata.com/ddp/v1/transactions/{{merchantCustomerId}}
### Sample Request
This request is empty since it’s a GET call