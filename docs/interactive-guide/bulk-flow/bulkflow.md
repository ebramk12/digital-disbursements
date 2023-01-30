
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
Accessing Client Line Enterprise
Bulk is accessible to clients via Client Line Enterprise to those users who have been assigned the correct entitlements.
Step 1:   Open the Business Track link.

Step 2:  Select the ‘Merchant’ log in option

[![Clx Login](../../../../assets/images/clx.png)]

Step 3:  Enter your user name and password


If you do not have a user name and password, please contact your account manager or the administrator for your company.


Step 4:   Enter the security code that was sent to your email.  The email address used is the same email where you received your log in credentials from Business Track.


Step 5:   Select the ‘Client Line Enterprise’ option under the Administration drop down box.


Step 6:   Select the entity for which you will be processing the BULK file.

