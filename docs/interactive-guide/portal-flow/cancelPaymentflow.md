#Description

Merchant can only cancel payments that are in a “Pending” status. Once a disbursement method has been selected by the recipient, the payment is no longer able to be cancelled. After disbursement cancellation only applicable to ACH.

Clients are able to initiate a payment cancellation at any time during the process, unless the disbursement is being processed.   When a cancellation is successful:

The Transaction and Payment statuses are updated

The hold is removed from the funds in the DFA

Notification is sent to the recipient(s)


[![Try it out](../../../../assets/images/button.png)](../api/?type=patch&path=/ddp/v1/payments/{id}/cancel)