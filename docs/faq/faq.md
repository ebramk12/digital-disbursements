# How we can help you? 

**Here are few common questions that may help you while you are exploring our API.**

### General FAQs

<details>
<summary><b>What are the recipient types available for digital disbursement payments?</b></summary>

There are 2 recipient types – Consumer and Company.

</details>

<details>
<summary><b>Is the user experience in the portal different once payment notification goes out between a consumer and business?</b></summary>

No, both will have same user experience.

</details>

<details>
<summary><b>What is TIN? Also, which use case involves passing value for TIN?</b></summary>

TIN (Taxpayer Identification Number) here refers to TIN of the business recipient. This is mandatory for business recipient.

</details>


### Customer Services FAQs

<details>
<summary><b>What are the IPS to be whitelisted for webhooks by client?</b></summary>

204.194.141.0/24
204.194.143.0/24

Subnet(/24) will cover a total of 256 ips (204.194.143.0 - 204.194.143.255).

Note : If any difficulties whitelisting the above IPS please use below ones

204.194.141.29 204.194.141.30 204.194.143.29 204.194.143.30

</details>


### Account Services FAQs

<details>
  <summary><b>Is the mobile number mandatory for create recipient?</b></summary>

No. 

</details>


### Payment Services FAQs 


<details>
<summary><b>How should we differentiate between a declined payment response?</b></summary>

You can differentiate based on the error codes, but the best way to get the payment status is using our [GET API] (../api?type=get&path=/ddp/v1/transactions/{transactionId}) request for transactions
  
</details>


### Security FAQs

<details>
<summary><b>What kind of fraud check mechanism exists?</b></summary>

We have vigilance Fraud check is enabled, which means any suspicious card or account will be declined for disbursements.

</details>



[//]: # (These are reference links used in markdown file)

[Setup Tenant]: <?path=docs/getting-started/setup-tenant/setup-tenant.md>

[Register Tenant]: <?path=docs/getting-started/setup-tenant/register-tenant.md>

[Deploy Tenant]: <?path=docs/getting-started/setup-tenant/deploy-tenant.md>

[Sample tenant repo]: <https://github.com/fiserv/sample-tenant>





## Some frequently asked questions

[What are the recipient types available for digital disbursement payments?](?path=docs/faq/ans/recipientTypes.md)

[Is the user experience in the portal different once payment notification goes out between a consumer and business?](?path=docs/faq/ans/usrExp.md)

[How should we differentiate between a declined payment response?](?path=docs/faq/ans/dpr.md)

[What is TIN? Also, which use case involves passing value for TIN](?path=docs/faq/ans/tin.md)

[Since merchantCustomerID is unique to the customers ,does that mean if the same customer has made withdrawals multiple times, then when we disburse to the customer, the merchantCustomerID will be the same?](?path=docs/faq/ans/uniquMCID.md)

[Is the mobile number mandatory for create recipient?](?path=docs/faq/ans/isMobile.md)

[Why is Consumer recipient GUEST value is passed as True? Why is this required when posting the recipient?](?path=docs/faq/ans/recipientGuest.md)

[What are Recipient Identifier Types? How are they used in integration for Consumer?](?path=docs/faq/ans/recipientIdentifier.md)

[What are the IPS to be whitelisted for webhooks by client?](?path=docs/faq/ans/webhookIP.md)

[Do DDP support HMAC in web hook notification?](?path=docs/faq/ans/webhookNotification.md)

[What is the process for generating and agreeing about the secret key for the HMAC to secure the notifications?](?path=docs/faq/ans/hmacgeneration.md)

[What is the process for generating and agreeing about the secret key for the HMAC to secure the notifications?](?path=docs/faq/ans/environmentURL.md)

[Do we receive a response and notification at the same time (if we send a POST Payment request do we expect to receive a response and to be notified also for that status)?](?path=docs/faq/ans/notificationResponse.md)

[What kind of fraud check mechanism exists?](?path=docs/faq/ans/fraudcheck.md)

[Is there any transaction limits for a individual recipient?] (?path=docs/faq/ans/recipientLimit.md)

[What are all custom fields available in payment Request?] (?path=docs/faq/ans/customFields.md)


