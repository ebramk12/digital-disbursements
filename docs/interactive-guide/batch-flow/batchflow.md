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
>**"amount.value","amount.currency","merchantId","merchantCustomerId","paymentType","recipient.type","recipient.email","recipient.firstName","recipient.lastName","recipient.dob","recipient.tin","recipient.phone.value","recipient.phone.ext","recipient.address.street","recipient.address.city","recipient.address.state","recipient.address.postalCode","recipient.address.country","recipient.dba","merchantTransactionId","customFields.recipient"

##Mapping Details

| Field Name 		  | Datatype  | Maximum Length | Required | Comments |
| ------------------- | --------- | ---------------| ---------| ------------------------------------- |
| `AMOUNT` 			  |  String	  |				   | &#10004;	| amount to be used to initiate payment |
| `CURRENCY` 		  |  String	  |		 		   |  		| currency used to initiate the payment. default is set to USD if value is not present |
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
>**<ACTION_CODE>|<MERCHANT_ID>|<MERCHANT_CUSTOMER_ID>|<MERCHANT_TRANSACTION_ID>|<STATUS_CODE>|<STATUS_DESCRIPTION>

| Field Name 		  | Datatype  | Comments |
| ------------------- | --------- | ------------------------------------- |
| `ACTION_CODE` 	  |  String	  |	identify the action performed initiate payment, cancel payment, etc. |
| `MERCHANT_ID` 	  |  String	  |	merchant who initiated the request |
| `MERCHANT_CUSTOMER_ID OR VENDOR_ID` |  String	  |	merchant recipient mapping id  |
| `MERCHANT_TRANSACTION_ID` |  String |	Reference ID sent by merchant during payment initiation |
| `STATUS_CODE` 	  |  String	  |	This will be code return via api. For success we'll use 00 but for error we'll pass actual error code received from API eg. 400011|
| `STATUS_DESCRIPTION`|  String	  |	For Success value will be SUCESS and for error it will be reason of API failure. eg. Invalid email id|

FH|||1234|
BH|1
CI|000000000000|21WSR00053.3781622.6792411.88000005|21WSR00053.3781622.6792411.88000005|00|SUCCESS|
CI|000000000000|21WSR00053.3781623.6792410.88000006|21WSR00053.3781623.6792410.88000006|00|SUCCESS|
CI|000000000000|21NCL01140.3781594.6782806.88000007|21NCL01140.3781594.6782806.88000007|00|SUCCESS|
CI|000000000000|21NCL00912.3781596.6779034.88000008|21NCL00912.3781596.6779034.88000008|00|SUCCESS|
CI|||||269902|RecordIndex=4;ValidationError=totalFieldCount violation; expected=22 actual=21
CI|000000000000|21OCE00046.3781600.6784934.88000010|21OCE00046.3781600.6784934.88000010|00|SUCCESS|
CI|000000000000|21OCE00042.3781602.6780781.88000011|21OCE00042.3781602.6780781.88000011|00|SUCCESS|
CI|000000000000|21PCT00821.3781607.6790810.88000012|21PCT00821.3781607.6790810.88000012|00|SUCCESS|
CI|000000000000|21WSR00051.3781621.6791379.88000004|21WSR00051.3781621.6791379.88000004|00|SUCCESS|
BT|9|8|1
FT|1|8|1
