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

| Field Name 		  | Datatype  | Maximum Length | Required | Comments |
| ------------------- | --------- | ---------------| ---------| ------------------------------------- |
| `AMOUNT` 			  |  String	  |				   | &#10004;	| amount to be used to initiate payment |
| `CURRENCY` 		  |  String	  |		 		   | No 		| currency used to initiate the payment. default is set to USD if value is not present |
| `MERCHANT_ID` 	  | String	  |		 32		   | &#10004;	| merchant who initiated the request |
| `MERCHANT_CUSTOMER_ID OR VENDOR_ID` | String  |	 32  | &#10004;	| merchant who initiated the request |
| `PAYMENT_TYPE OR DISBURSEMENT_TYPE` | String  |  20 | &#10004;	| free text - Type of disbursement - Wages, Claims, promotions,Loans, refund etc- refer the extract taken from QA environment "types-of-payment-types.txt"  |
| `RECIPIENT_TYPE` 	  |  String	|		 			| &#10004;	| recipient type. possible values Consumer/Company |
| `EMAIL` 			  |  String	|		 			| &#10004;	| recipient email address |
| `FIRST_NAME` 		  |  String	|		 			| Conditional 	| recipient first name should be sent if the recipient type is "Consumer" |
| `LAST_NAME` 		  |  String	|		 			| Conditional 	| recipient last name should be sent if the recipient type is "Consumer" |
| `DATE_OF_BIRTH` 	  |  String	|		 			| Conditional 	| Value should be empty |
| `TIN` 			  |	 String	|		 			| Conditional 	| TIN should be sent if the recipient is "Company" |
| `PHONE_NUMBER`	  |  String	|		 			| 				| Value should be empty |
| `PHONE_NUMBER_EXTENSION` |  String  |		 		| 				| Value should be empty |
| `STREET` 			  | String	|		 			| &#10004;	| recipient address street|
| `CITY` 			  |	String	|					| &#10004;	| recipient city street |
| `STATE`			  | String	|		 			| &#10004;	| recipient state street |
| `POSTAL_CODE` 	  | String	|		 			| &#10004;	| recipient address postal code|
| `COUNTRY` 		  | String	|		 			| &#10004;	| recipient address country |
| `DBA`				  | String	|   				| Conditional | DBA should be sent if the recipient Company name  |
| `MERCHANT_TRANSACTION_ID OR REFERENCE_ID` | String	|	| &#10004;	| unique for each request |
| `CUSTOM_FIELDS` 	  |	String	|				    | 			| optional and value will be list of key value pairs(key and value pairs will be delimited by colon( : )) and delimited by comma(,) |


