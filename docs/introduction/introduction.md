# Introduction

DDP is a payment platform that enables business to send payments to your customers, the digitized payments reduce the friction and time required for your customers to recieve the money. 

Fiserv’s Digital Disbursement product allows merchants to provide customers with 
fast, more secure and cost-effective payout options how and when they 
want – on weekends, holidays and after hours. ikewise, the product allows the recipient to select the method to be used to disburse the payment.

Flowchart LR
    A[Create Recipient] --> B([Get Encryption Key])
    B --|Encrypt Card Data|> c[Request Nonce Token]

---

# Integration Options

Digital Disbursements allows several flexible integration options to make onboarding easy and accessible.

<!-- type: row -->

<!-- type: card
title: Payments Portal
Description: Disburse payouts through the most popular channels to multiple recipients and create custom configurations in a Client-branded Portal
link: ?path=docs/interactive-guide/api-flow/initiateportalflow.md
-->

<!-- type: card
title: Hosted Payments Page
description: Offers the use of a client-branded iframe to facilitate sending account infomration to Fiserv and the merchant will recieve a multi-use token for future use.
link: ?path=docs/interactive-guide/api-flow/hosted-pages.md
-->

<!-- type: card
title: API Only
description: With our easy to use APIs you can create your own unique user experiance with the confidence of a secure and fast Payments backend.
link: ?path=docs/interactive-guide/api-flow/apiflow.md
-->

<!-- type: card
title: Batch and Bulk Options
description: Simply upload a file with payment data via a Maganged File Gateway or Fiserv's ClientLine Enterprise reporting suite. Once Uploaded Fiserv systems will read the file and complete the 
-->

<!-- type: row-end --> 