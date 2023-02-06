
# PORTAL Flow

Digital Disbursement clients are allowed to determine if the recipient should be allowed to register on the recipient portal or not.  Typically, the decision is based on the number of times that a consumer/business is expected to receive a payment. 

DDP allow two types of recipient flow.

• Guest

• Register

**<ins> Guest </ins>**

If the payment is a one-time event, then the guest option is used.  

**<ins> Register </ins>**

If more than one payment is expected to be sent to the recipient, then registration is requested.

**<ins> Multiple Recipient Payments  </ins>**

Recipients determine who will receive the funds:   If this option is being used, then the first recipient to enter his/her disbursement information will receive all of the funds.  The remaining recipients will have to approve the disbursement to the recipient receiving the funds prior to the completion of the disbursement.  If the payment expires before all recipients have approved or a recipient rejects the payment, then the payment is cancelled, funds are released in the DFA, and recipients are notified of the expiration.

DDP Merchant can initiate the below type of payment Initiation for recipient.

## Initiate Single Consumer Payment

Objective Merchant will want to initiate a payment for a single consumer recipient through the merchant portal and send email to recipient for the payment disbursement.

[![Try it out](../../../../assets/images/button.png)](../api/?type=post&path=/ddp/v1/payments)

## Initiate Single Company Payment

Objective Merchant will want to initiate a payment for a single company recipient through the merchant portal and send email to recipient for the payment disbursement.

[![Try it out](../../../../assets/images/button.png)](../api/?type=post&path=/ddp/v1/payments)

## Initiate Multi Consumer Payment

Objective Merchant will want to initiate a payment for a Multi consumer recipient through the merchant portal and send email to recipient for the payment disbursement.

[![Try it out](../../../../assets/images/button.png)](../api/?type=post&path=/ddp/v1/payments)

## Initiate Multi Company Payment

Objective Merchant will want to initiate a payment for a Multi company recipient through the merchant portal and send email to recipient for the payment disbursement.

[![Try it out](../../../../assets/images/button.png)](../api/?type=post&path=/ddp/v1/payments)

## Cancel

**<ins> Description </ins>**

Merchant can only cancel payments that are in a “Pending” status. Once a disbursement method has been selected by the recipient, the payment is no longer able to be cancelled. After disbursement cancellation only applicable to ACH, Coinbase, E-check, Venmo and PayPal.

Clients are able to initiate a payment cancellation at any time during the process, unless the disbursement is being processed. When a cancellation is successful:

• The Transaction and Payment statuses are updated.

• The hold is removed from the funds in the DFA.

• Notification is sent to the recipient(s).

[![Try it out](../../../../assets/images/button.png)](../api/?type=patch&path=/ddp/v1/payments/{id}/cancel)

**<ins> Description </ins>**

## Get Merchant Info

This request will get the details of the onboarded merchant with no request parameter only the headers are required. With this call you can get the full information of the merchant like ledger balance, Available balance, DFA Account Number, Merchant Name & Address details etc.

[![Try it out](../../../../assets/images/button.png)](../api/?type=get&path=/ddp/v1/merchantInfo)

## See Also

- [Please refer our FAQ's](?path=docs/faq/faq.md&branch=develop#portal-flow-faqs)