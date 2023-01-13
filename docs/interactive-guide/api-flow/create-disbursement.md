## Step 5: Create a Disbursement

### Description
This request will take our `enrolment_vault` token and use it to create a disbursement payment for a customer. The key variables here are `merchantTransactionId`, this must be unique for every transaction call and can be used in step 5a, as well as paymentType which should correspond to the paymentType associated with your environment.