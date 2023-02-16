#Webhook Notifications

Description: 
A webhook is essentially the same as any web page URI.  It's a client-specific URI for incoming HTTP POST notification messages.  Responses should be a standard 2xx HTTP response code and anything else would be considered a failure and subject to a retry POST. In this mechanism, consumer application exposes an endpoint and when the producer application has any updated information, it sends a message to a consumer application over URL. The communication between the two applications is Asynchronous and nonblocking. Webhooks are much like SMS notifications. Say your bank sends you an SMS for any transaction. You already told the bank your phone number, so they knew where to send the message.  


Endpoint URL: 
Client must provide the merchant_endpoint and the suggest URL is https://<<merchant_endpoint>>/payments/notification. DDP will be able to support Basic Authorization or HMAC for verifications. The endpoint URL should be provided by client for non-production & production respectively. Automated notifications will be posted by DDP on pre-configured payment status. The list of pre-configured notification events shared with clients as part of the onboarding form to choose 




| Feature Name |Description|
| ------------------ |  ---------- |
|	ENABLE_WEBHOOK_ACH_SALE_REVERSAL	| 	Triggered when the ACH reversal process is successful	| 
| 	ENABLE_WEBHOOK_ACH_SALE_REVERSAL_FAILED	| 	Triggered when the ACH reversal process is NOT successful	| 
| 	ENABLE_WEBHOOK_ACH_CANCEL_SALE_REVERSAL	| 	Triggered when the ACH transaction is successfully cancelled.	| 
| 	ENABLE_WEBHOOK_DISBURSEMENT_FAILED	| 	Triggred when a payment has NOT been successfully disbursed using the recipient's chosen selection	| 
| 	ENABLE_WEBHOOK_FRAUD_HOLD	| 	Triggered when a payment is placed on Fraud Hold and is not sent to the recipient.	| 
| 	ENABLE_WEBHOOK_PAYMENT_CANCELLED	| 	Triggered when a payment status is successfully changed to cancelled.	| 
| 	ENABLE_WEBHOOK_PAYMENT_REJECTED	| 	Triggered when a recipient rejects the payment.	| 
| 	ENABLE_WEBHOOK_PAYMENT_EXPIRED	| 	Triggered when a pending payment expires and is no longer able to be disbursed.	| 
| 	ENABLE_WEBHOOK_PAYMENT_DISBURSED	| 	Triggered when a payment is disbursed.	| 
| 	ENABLE_WEBHOOK_PAYMENT_SELECTED	| 	Enable web hook to merchant when payment method is selected by recipient	| 
| 	ENABLE_WEBHOOK_ACH_CREDIT_REJECT	| 	Triggered when an ACH Disbursement is rejected. 	| 
| 	ENABLE_WEBHOOK_PAYMENT_SELECTED_CANCELLED	| 	triggerred when a payment has been rejected by a recipient	| 
| 	ENABLE_WEBHOOK_ACH_CANCELLED	| 	Triggered when an ACH disbursement is successfully canceled.	| 
| 	ENABLE_WEBHOOK_EMAIL_BOUNCED	| 	Triggered when an email notification sent to a recipient bounces back.  The notification considered is payment initiation.	| 
| 	ENABLE_DFA_BALANCE_WEBHOOK_ALERT	| 	Triggered when the DFA balance meets or drops below a set balance	| 
| 	ENABLE_WEBHOOK_PAYMENT_PROCESSING	| 	Enable web hook to merchant when Venmo/Paypal payment is disbursed.	| 
| 	ENABLE_WEBHOOK_VENMO_CREDIT_REJECT	| 	Enable Webhook to Merchant When payment is rejected by the payer.	| 
| 	ENABLE_WEBHOOK_VENMO_CANCELLED	| 	Webhook to merchant for unclaimed status	| 
| 	ENABLE_WEBHOOK_VENMO_DISBURSEMENT_UNCLAIMED	| 	Webhook to merchant for unclaimed status	| 
| 	ENABLE_WEBHOOK_VENMO_DISBURSEMENT_FAILED	| 	Webhook to merchant for Failed status	| 
| 	ENABLE_WEBHOOK_VENMO_PAYPAL_PAYMENT_DISBURSE_HELD	| 	Enable web hook to merchant when Venmo/Paypal payment is held.	| 
| 	ENABLE_WEBHOOK_VENMO_DISBURSEMENT_BLOCKED	| 	Enable web hook to merchant when Venmo/Paypal payment is blocked	| 
| 	ENABLE_WEBHOOK_CHECK_DISBURSEMENT_PRINTED	| 	webhook to merchant after receiving printed webhook from chekbook.io	| 
| 	ENABLE_WEBHOOK_PAYMENT_ECHECK_DISBURSED	| 	Enable webhook when Echeck payment is disbursed.	| 
| 	ENABLE_WEBHOOK_CHECK_REVERSAL_SUCCESS	| 	Webhook to merchant for reversal success	| 
| 	ENABLE_WEBHOOK_CHECK_REVERSAL_FAIL	| 	Webhook to merchant for reversal fail	| 
| 	ENABLE_WEBHOOK_BATCH_ACKNOWLEDGEMENT	| 	Webhook to merchant for Batch Acknowledgement	| 
| 	ENABLE_WEBHOOK_BATCH_SUMMARY	| 	Webhook to merchant for Batch Summary	| 