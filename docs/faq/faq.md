# How we can help you? 

**Here are few common questions that may help you while you are exploring our API.**

### General FAQs

<details>
<summary><b>What are the recipient types available for digital disbursement payments?</b></summary>

DDP supports 2 recipient types – Consumer and Company.

Consumer is an individual or a person. Company is usually a business or business user.

</details>

<details>
<summary><b>What is TIN? Also, which use case involves passing value for TIN?</b></summary>

TIN (Taxpayer Identification Number) here refers to TIN of the business recipient. This is mandatory for business recipient.

</details>

<details>
  <summary><b>Is the mobile number mandatory for create recipient?</b></summary>

No, the mobile number is not the mandatory parameters for creating the recipient.

</details>

<details>
<summary><b>Will we receive a response and notification at the same time (if we send a POST Payment request do we expect to receive a response and to be notified also for that status)?</b></summary>

HTTP Responses are mostly synchronous and immediate. Notification based on the event can be immediate or time dependent. In the above scenario if notification is configured for the payment request, we will receive both at the same time. For more information on Notification please refer notification [section].

</details>

<details>
<summary><b>Can you elaborate on how a retry is initiated? What is the maximum retry count? </b></summary>

When recipient provides wrong payment information (Payment will be declined by backend as payment info is wrong) for fixed number of times then payment is cancelled when max retry attempt is reached.

How many times a recipient can attempt to disburse a payment with wrong payment information can be configured by using key ENABLE_PAYMENT_RETRY_COUNT.

</details>

<details>
<summary><b>Is “TV – Transaction Cancelled”, “DNF - Delivery Notification Failed” a final state? Should we VOID this payment? Or will this eventually become expired or another status? </b></summary>

This is final state and can be considered as payment cancelled. No need to VOID or any other action required. For more info please refer [Payment Status] (../docs/?path=docs/troubleshooting/Transaction-payment-status.md)

</details>

<details>
<summary><b>How do we setup to get webhook notifications back from Fiserv in our lower environments? </b></summary>

We must raise a firewall request from Fiserv side, which can take some time. So, the URL for this should be given at time of onboarding itself.

</details>

<details>
<summary><b>Is there a DDP web console for checking transaction results or attempts like we have with IPG? </b></summary>

 There is nothing like this available for non-prod. For production we have the CLX reporting tool.  

</details>

<details>
<summary><b>Can you provide us all possible code values for each expected payment status “DH”, “DD” and “DF”? </b></summary>

DD & DH is only applicable and the possible values are  

400063  DH Fraud Failed 

400201  DD D2D payment declined by PaySecure. For more info please refer [Error Codes] (../docs/?path=docs/troubleshooting/error-codes.md) and
[Payment Status] (../docs/?path=docs/troubleshooting/Transaction-payment-status.md)


</details>

<details>
<summary><b>What are the IPS to be whitelisted for webhooks by client?</b></summary>

204.194.141.0/24
204.194.143.0/24

Subnet(/24) will cover a total of 256 ips (204.194.143.0 - 204.194.143.255).

Note : If any difficulties whitelisting the above IPS please use below ones

204.194.141.29 204.194.141.30 204.194.143.29 204.194.143.30

</details>

### API Flow FAQs

<details>
<summary><b>What should be supplied as tokenId to the payments with tokenProvider as ENROLMENT_VAULT?</b></summary>

Enrollment Vault Id should be supplied as part of the payment request. It is the token we get back from accounts. For more info please refer [API Flow] (../docs/?path=docs/interactive-guide/api-flow/apiflow.md)

</details>

<details>
<summary><b>What are all custom fields support available in payment request?</b></summary>

There is no limit for custom fields in payment request. we can add as many as required.

</details>

<details>
  <summary><b>Why is Consumer recipient GUEST value is passed as True? Why is this required when posting the recipient?</b></summary>

If Guest is false for Recipient of type Consumer, then payment cannot be initialized for the recipient as it will be considered as an INACTIVE recipient. 

</details>


### Portal Flow FAQs

<details>
<summary><b>Is the user experience in the portal different once payment notification goes out between a consumer and business?</b></summary>

No, both will have same user experience. For more info please refer [Portal Flow] (../docs/?path=docs/interactive-guide/portal-flow/portalflow.md)

</details>

<details>
<summary><b> Can a merchant cancel (“TV – Transaction Cancelled”, “PC- Payment Cancelled”) a payment from an Admin access to the portal? </b></summary>

Portal is only for recipients and Merchant cannot cancel a payment using portal.  

</details>

<details>
<summary><b>The source, tokenprovider and tokened are listed as required. Would we be passing any of the card source or maintaining tokens for this integration. Can you clarify these parameters? </b></summary>

You would just need to call initiate payment which would contain the information about the recipients, the amount, and merchantTransactionID. There is no need to call recipient as the portal will handle that. Only the initiate payment needs.

</details>

### Payment Services FAQs


<details>
<summary><b>How should we differentiate between a declined payment response?</b></summary>

You can differentiate based on the error codes, but the best way to get the payment status is using our [GET API] (../api?type=get&path=/ddp/v1/transactions/{transactionId}) request for transactions
  
</details>

<details>
<summary><b>Will you return the original ISO response codes from issuer/card scheme in the response for a POST /ddp/v1/payments </b></summary>

ISO response + DDP internal response code.

</details>

### Security FAQs

<details>
<summary><b>What kind of fraud check mechanism exists?</b></summary>

We have vigilance Fraud check is enabled, which means any suspicious card or account will be declined for disbursements.

</details>

<details>
<summary><b>Do DDP support HMAC in web hook notification?</b></summary>

Currently we don’t support the HMAC in webhook notification, we do support basic authentication in which a key value can be passed as part of header information, we will update the implementation guide accordingly.

</details>

<details>
<summary><b>What is the process for generating and agreeing about the secret key for the HMAC to secure the notifications?</b></summary>

Below are the way which we are using to generate the signature, you may also use the same. var key = postman.getEnvironmentVariable('clientId'); var secret = postman.getEnvironmentVariable('clientSecret');

var time = new Date().getTime(); var method = request.method;

var rawSignature = key + ":" + time; var requestBody = request.data;

if (method != 'GET' && method != 'DELETE') { var payload_digest = CryptoJS.SHA256(requestBody); var b64BodyContent = CryptoJS.enc.Base64.stringify(payload_digest); rawSignature = rawSignature + ":" + b64BodyContent; }

var signature = CryptoJS.HmacSHA256(rawSignature, secret); postman.setEnvironmentVariable('time', time); postman.setEnvironmentVariable('signature', CryptoJS.enc.Base64.stringify(signature));

</details>



[//]: # (These are reference links used in markdown file)

[Setup Tenant]: <?path=docs/getting-started/setup-tenant/setup-tenant.md>

[Register Tenant]: <?path=docs/getting-started/setup-tenant/register-tenant.md>

[Deploy Tenant]: <?path=docs/getting-started/setup-tenant/deploy-tenant.md>

[Sample tenant repo]: <https://github.com/fiserv/sample-tenant>