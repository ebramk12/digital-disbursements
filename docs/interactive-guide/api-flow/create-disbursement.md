## Step 5: Create a Disbursement

### Description
This request is the payment call where we will take our `enrolment_vault` token and use it to create a disbursement payment for a recipient. The key variables here are `merchantTransactionId`, this must be unique for every transaction call , as well as paymentType which should correspond to the payment type associated with your environment for eg. Gaming, Claims, Wages etc.