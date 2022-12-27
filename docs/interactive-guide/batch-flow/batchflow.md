																#BATCH FILE
																
# File Name Standard

•	Merchant should upload files to SFTP location with below file name pattern. Each segment is separated by dot (.)
•	FLXBAT.{FLEX_MID}.{TYPE}.{EPOCH}.{NAME}.{VERSION}.{EXT}. Sample File name : FLXBAT.NMM.CI.1654537809.BAT97.1.csv

The below table identifies the parameters of File format.

| Variable | Description | Ex |
| -------- | ------------------ | ------- |
| `FLXBAT` | Static Prefix |  |
| `FLEX_MID` | Alpha Numeric Flex MID provided to merchant at the time of onboarding | SF,NMM |
| `TYPE` | 2 letter record type from below list | CI |
| `EPOCH` | number of seconds that have elapsed since January 1, 1970 (midnight UTC/GMT) | 1654537809 |
| `NAME` | merchant preferred alpha-numeric (label or name) max-length : 20 | STLMNT220510 batch93 |
| `VERSION` | file version as integer. | 1 |
| `EXT` | file extension | CI |

•	Depending on DB and Git Configurations Flex Reader will pick files from SFTP Location.

## Batch Flex config

##Headers
"amount.value","amount.currency","merchantId","merchantCustomerId","paymentType","recipient.type","recipient.email","recipient.firstName","recipient.lastName","recipient.dob","recipient.tin","recipient.phone.value","recipient.phone.ext","recipient.address.street","recipient.address.city","recipient.address.state","recipient.address.postalCode","recipient.address.country","recipient.dba","merchantTransactionId","customFields.recipient"

##Mapping Details

| Field Name | Position | Datatype | Length | Required | Comments |
| -------- | -------| --------- | -------| ---------| ------------------------------------- |
| `AMOUNT` |  		|   		|		 | Yes 		| amount to be used to initiate payment |
| `CURRENCY` |  		|   		|		 | No 		| currency used to initiate the payment. default is set to USD if value is not present |
| `MERCHANT_ID` |  		|   		|		 | Yes 		| merchant who initiated the request |
| `MERCHANT_CUSTOMER_ID OR VENDOR_ID` |  		|   		|		 | Yes 		| merchant who initiated the request |
| `PAYMENT_TYPE OR DISBURSEMENT_TYPE` |  		|   		|		 | Yes 		| free text - Type of disbursement - Wages, Claims, promotions,Loans, refund etc- refer the extract taken from QA environment "types-of-payment-types.txt"  |
| `RECIPIENT_TYPE` |  		|   		|		 | Yes 		| recipient type. possible values Consumer/Company |
| `EMAIL` |  		|   		|		 | Yes 		| recipient email address |
| `FIRST_NAME` |  		|   		|		 | Conditional 		| recipient first name should be sent if the recipient type is "Consumer" |
| `LAST_NAME` |  		|   		|		 | Conditional 		| recipient last name should be sent if the recipient type is "Consumer" |
| `DATE_OF_BIRTH` |  		|   		|		 | Conditional 		| Value should be empty |
| `TIN` |  		|   		|		 | Conditional 		| TIN should be sent if the recipient is "Company" |

| `PHONE_NUMBER` |  		|   		|		 | Optional 		| Value should be empty |
| `PHONE_NUMBER_EXTENSION` |  		|   		|		 | Optional 		| Value should be empty |
| `STREET` |  		|   		|		 | Yes 		| recipient address street|
| `CITY` |  		|   		|		 | Yes 		| recipient city street |
| `STATE` |  		|   		|		 | Yes 		| recipient state street |
| `POSTAL_CODE` |  		|   		|		 | Yes 		| recipient address postal code|
| `COUNTRY` |  		|   		|		 | Yes 		| recipient address country |
| `DBA` |  		|   		|		 | Conditional 		| DBA should be sent if the recipient Company name  |
| `MERCHANT_TRANSACTION_ID OR REFERENCE_ID` |  		|   		|		 | Yes 		| unique for each request |
| `CUSTOM_FIELDS` |  		|   		|		 | No 		| optional and value will be list of key value pairs(key and value pairs will be delimited by colon( : )) and delimited by comma(,) |


