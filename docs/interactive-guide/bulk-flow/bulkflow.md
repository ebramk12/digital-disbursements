
# Introduction
This guide documents the BULK tool as used by the Digital Payout product.   The BULK tool allows clients to initiate and manage large numbers of payments through an easy-to-use online interface.   Below is a list of tasks for which the BULK option is available:

•	Creating a Recipient

•	Initiating a Payment

•	Cancelling a Payment

•	Create a Recipient & Initiate a Payment

## How the Bulk Process Works

The process begins with the creation of a bulk template.  Once the template has been created and entered/uploaded into Client Line Enterprise, the information is sent to the Carat Digital Payout platform.   Once received by the Payout platform, the actions requested on the template are completed and all issues returned to Client Line Enterprise and displayed for the Merchant.
Please Note:  All Bulk templates are placed into a queue upon arrival on the Payout platform.   The bulk files are completed based on their position in the queue.
Bulk Template

The purpose of the Bulk Template is to allow a merchant the option of sending more than one record to the Carat Digital Payout platform for processing at a time.   The benefit of using this template is to allow clients the option of using the Digital Payout product with very little to no development required on their part. 

A Comma Separated Values (.csv) file is created by the client and uploaded to the BULK product in Client Line Enterprise.  In BULK, a line item is created for each action that is to be performed.  Please note:   The maximum number of line items for a single file is 1000.
Clients have two options for creating a bulk template:

1.	Manually create the template and upload the document into CLX
2.	Utilize the Bulk screens within CLX to create the template
Please remember:   Bulk templates are only able to include action types for a single MID at a time.   This means that each template may only include line items that pertain to one MID.

## Client Line Enterprise

### Accessing Client Line Enterprise
Bulk is accessible to clients via Client Line Enterprise to those users who have been assigned the correct entitlements.
Step 1:   Open the Business Track link.

Step 2:  Select the ‘Merchant’ log in option

[![Clx](../../../../assets/images/clx.png)]

Step 3:  Enter your user name and password

[![Clx Login](../../../../assets/images/clxlogin.png)]

If you do not have a user name and password, please contact your account manager or the administrator for your company.

Step 4:   Enter the security code that was sent to your email.  The email address used is the same email where you received your log in credentials from Business Track.

[![Clx Security](../../../../assets/images/clxsecurity.png)]

Step 5:   Select the ‘Client Line Enterprise’ option under the Administration drop down box.

[![Clx Admin](../../../../assets/images/clxAdmin.png)]

Step 6:   Select the entity for which you will be processing the BULK file.

[![Clx Bulk](../../../../assets/images/clxbulk.png)]

### Accessing BULK

Step 1:	Select the option “Bulk Upload” from the menu on the left hand side of the screen

[![Clx BulkUpload](../../../../assets/images/bulkupload.png)]

## Bulk Actions

### Creating a Recipient

This action is used by clients who need to associate recipients to their MID.   Recipients must be associated to the MID prior to the initiation of a payment.  
If you wish to use the BULK method to create recipients, you will need to initiate the process under the Bulk Upload Menu.

Step 1:  Select the “New Recipient Bulk Upload” option.

[![New RecipientBulk](../../../../assets/images/newRecipientBulk.png)]

Step 2:  Determine if you want to upload a template or create a single line item and select the correct option.

[![Create Singleline](../../../../assets/images/createsingleline.png)]

#### Add a Recipient:  Single Line Option

Step 1:  Select the “Add New” Button

[![Add New](../../../../assets/images/addNew.png)]

Step 2:  Complete all required fields and any optional fields that are needed.

[![bulkload](../../../../assets/images/bulkload.png)]

Step 3:  Select the “Add Button” if additional line items are needed.

[![Add Button](../../../../assets/images/addButton.png)]

Step 4:  When all line items have been added, select the “Process Transaction” button.   Please Note:  The “Process Transaction” button is not enabled if there are any errors found within the line items that have been entered.

[![Transaction](../../../../assets/images/processTransaction.png)]

Step 5: Once the confirmation has been displayed, the file will have been included in a batch for processing by DDP.

[![Confirmation](../../../../assets/images/confirmation.png)]