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
<!-- theme: success -->
>"amount.value","amount.currency","merchantId","merchantCustomerId","paymentType","recipient.type","recipient.email","recipient.firstName","recipient.lastName","recipient.dob","recipient.tin","recipient.phone.value","recipient.phone.ext","recipient.address.street","recipient.address.city","recipient.address.state","recipient.address.postalCode","recipient.address.country","recipient.dba","merchantTransactionId","customFields.recipient"

##Mapping Details

| Field Name 		  | Datatype  | Maximum Length | Required       | Comments |
| ------------------- | --------- | ---------------| ---------------| --------------------------------------------------------------------		|
| `AMOUNT` 			  |  String	  |		(16,4) 	   | &#10004;		| amount to be used to initiate payment 									|
| `CURRENCY` 		  |  String	  |		 20    	   | &#10004;		| currency used to initiate the payment. default is set to USD 				|
| `MERCHANT_ID` 	  | String	  |		 32		   | &#10004;		| merchant who initiated the request 										|
| `MERCHANT_CUSTOMER_ID OR VENDOR_ID` | String  |  32  | &#10004;	| merchant who initiated the request 										|
| `PAYMENT_TYPE OR DISBURSEMENT_TYPE` | String  |  20  | &#10004;	| free text - Type of disbursement - Wages, Claims, promotions,Loans etc"   |
| `RECIPIENT_TYPE` 	  |  String	|		100	        | &#10004;		| recipient type. possible values Consumer/Company 							|
| `EMAIL` 			  |  String	|		100			| &#10004;		| recipient email address 													|
| `FIRST_NAME` 		  |  String	|		100 		| Conditional 	| recipient first name should be sent if the recipient type is "Consumer"	|
| `LAST_NAME` 		  |  String	|		100 		| Conditional 	| recipient last name should be sent if the recipient type is "Consumer"	|
| `DATE_OF_BIRTH` 	  |  String	|		 			| Conditional 	| date of birth should be sent if the recipient is "Consumer"				|
| `TIN` 			  |	 String	|		10 			| Conditional 	| TIN should be sent if the recipient is "Company" 							|
| `PHONE_NUMBER`	  |  String	|		50			| Conditional	| recipient phone number													|
| `PHONE_NUMBER_EXTENSION` |  String  |		 		| 				| recipient phone number extension											|
| `STREET` 			  | String	|		200 		| &#10004;		| recipient address street													|
| `CITY` 			  |	String	|		50			| &#10004;		| recipient city street 													|
| `STATE`			  | String	|		50 			| &#10004;		| recipient state street 													|
| `POSTAL_CODE` 	  | String	|		20			| &#10004;		| recipient address postal code												|
| `COUNTRY` 		  | String	|		20 			| &#10004;		| recipient address country 												|
| `DBA`				  | String	|   				| Conditional 	| DBA should be sent if the recipient Company name  						|
| `MERCHANT_TRANSACTION_ID OR REFERENCE_ID` | String |	100  | &#10004;	| unique for each request 												|
| `CUSTOM_FIELDS` 	  |	String	|				    | 				| optional and value will be list of key value pairs(key and value pairs will be delimited by colon( : )) and delimited by comma(,) |


DDP will share thh two type of response
		1. Batch Summary email
		2. Batch Summary Output File

## Summary Email
DDP send the summary email of the below format to the corresponding merchant.

| Record Type 		| Description |
| ----------------	| ------------------------------------- 		  |
| `File Name` 	  	|	name of the processed file					  |
| `Total Records` 	|	No of records present in file. 				  |
| `Success Records` |	No of records which processed successfully.	  |
| `Failed records` 	|	No of records which failed during processing. |
| `Invalid records`	|	No of records which invalid during processing.|


##Batch Summary Output File
###Response File Headers

<!-- theme: success -->
> ACTION_CODE|MERCHANT_ID|MERCHANT_CUSTOMER_ID|MERCHANT_TRANSACTION_ID|STATUS_CODE|STATUS_DESCRIPTION

| Field Name 		  | Datatype  | Comments |
| ------------------- | --------- | ------------------------------------- |
| `ACTION_CODE` 	  |  String	  |	identify the action performed initiate payment, cancel payment, etc. |
| `MERCHANT_ID` 	  |  String	  |	merchant who initiated the request |
| `MERCHANT_CUSTOMER_ID OR VENDOR_ID` |  String	  |	merchant recipient mapping id  |
| `MERCHANT_TRANSACTION_ID` |  String |	Reference ID sent by merchant during payment initiation |
| `STATUS_CODE` 	  |  String	  |	This will be code return via api. For success we'll use 00 but for error we'll pass actual error code received from API eg. 400011|
| `STATUS_DESCRIPTION`|  String	  |	For Success value will be SUCESS and for error it will be reason of API failure. eg. Invalid email id|

##Example
FH|||1234|
BH|1
CI|000000000000|012345678|012345678|00|SUCCESS|
CI|000000000000|1324324324344|1324324324344|00|SUCCESS|
CI|000000000000|343543653656|343543653656|00|SUCCESS|
CI|000000000000|6587686786789|6587686786789|00|SUCCESS|
CI|||||269902|RecordIndex=4;ValidationError=totalFieldCount violation; expected=22 actual=21
CI|000000000000|8956565466666|8956565466666|00|SUCCESS|
CI|000000000000|7684543535543|7684543535543|00|SUCCESS|
CI|000000000000|4354654767677|4354654767677|00|SUCCESS|
CI|000000000000|8769789789879|8769789789879|00|SUCCESS|
BT|9|8|1
FT|1|8|1
