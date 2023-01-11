#Description

Objective Merchant will want to initiate a payment for a single company recipient through the merchant portal and send email to recipient for the payment disbursement.

---
##Endpoint

<!-- theme: success -->
 HTTP Method: **POST**

'Non-prod: https://int.api.firstdata.com/ddp/v1/payments'

>'Prod: https://prod.api.firstdata.com/ddp/v1/payments'
---

##Request Variables

| Name 					| 	Type 	| Maximum Length | Required  |
| --------------------- | -------	| ---------------|-------- 	 | 
| `Amount:currency` 	|  	String	| -				 |	&#10004; | 
| `Amount:total` 		|  	Number	| -				 |	&#10004; | 
| `merchantCustomerId` 	|  	String	| -				 |	&#10004; | 
| `recipientType` 		|  	String	| 32			 |  &#10004; | 
| `tin` 				|  	String	| -				 |	&#10004; | 
| `emailAddress` 		|  	String	| -				 |	&#10004; | 
| `phoneNumber`			|  	String	|  	 	  -		 |  		 |
| `recipientIdentifier` |  	String	| Accepted values [Last_4_of_SSN, SPECIAL_CODE, ACCOUNT_NUMBER, DATE_OF_BIRTH, PHONE_NUMBER] | &#10004; | 
| `recipientIdentifierValue` |  String	|-			 |	&#10004; |
| `address` 			|  	String	| -				 |	&#10004; | 
| `payments` 			|  	String	| -				 |	&#10004; | 
| `merchantTransactionId` |  String	| -				 |	&#10004; | 
| `batchNumber` 		|  	String	| -	  		 	 | 		 	 |
| `customFields` 		|  	String	| -		   		 | 			 |
| `doingBusinessAs` 	|  	String	| -				 |	&#10004; | 

## Headers

Content-Type:application/json <br>
Client-Request-Id:{{$guid}} <br>
Api-Key:{{clientKey}} <br>
Authorization:HMAC {{signature}} <br>
Timestamp:{{time}} <br>

## Sample Request (Minimal information)

```json
{
    "amount": {
        "total": 35,
        "currency": "USD"
    },
    "recipient": [
        {
            "recipientProfileInfo": {
                "recipientType": "Company",
                "merchantCustomerId": "test8977",
                "tin": "123456789",
                "emailAddress": {
                    "value": "gayathri@fiserv.com",
                    "type": "Work",
                    "primary": true
                },
                "phoneNumber": {
                    "code": 91,
                    "value": "704-884-2754",
                    "type": "billing",
                    "extension": "2145"
                },
                "recipientIdentifier": "SPECIAL_CODE",
                "recipientIdentifierValue": "9996663333",
                "doingBusinessAs": "Tech computers",
                "guest": false,
                "address": {
                    "type": "work",
                    "street": "100 Universal City Plaza",
                    "city": "Hollywood",
                    "stateOrProvince": "CA",
                    "postalCode": "91608",
                    "country": "USA",
                    "formatted": "100 Universal City Plaza, Hollywood, CA 91608 US",
                    "primary": true
                }
            },
            "payments": {
                "amount": {
                    "total": 35,
                    "currency": "USD"
                },
                "paymentType": "Claims"
            }
        }
    ]
}
```

## Sample Request (Additional Information)

```json
{
    "amount": {
        "total": 35,
        "currency": "USD"
    },
    "recipient": [
        {
            "recipientProfileInfo": {
                "recipientType": "Company",
                "merchantCustomerId": "test8977",
                "tin": "123456789",
                "emailAddress": {
                    "value": "gayathri@fiserv.com",
                    "type": "Work",
                    "primary": true
                },
                "phoneNumber": {
                    "code": 91,
                    "value": "704-884-2754",
                    "type": "billing",
                    "extension": "2145"
                },
                "recipientIdentifier": "SPECIAL_CODE",
                "recipientIdentifierValue": "9996663333",
                "doingBusinessAs": "Tech computers",
                "guest": false,
                "address": {
                    "type": "work",
                    "street": "100 Universal City Plaza",
                    "city": "Hollywood",
                    "stateOrProvince": "CA",
                    "postalCode": "91608",
                    "country": "USA",
                    "formatted": "100 Universal City Plaza, Hollywood, CA 91608 US",
                    "primary": true
                }
            },
            "payments": {
                "amount": {
                    "total": 35,
                    "currency": "USD"
                },
                "paymentType": "Claims"
            }
        }
    ],
    "merchantTransactionId": "merchantTransactionId-321540000011632",
    "batchNumber": "454567",
    "customFields": [
        {
            "key": "claim_number",
            "value": "3215406"
        },
        {
            "key": "incident_date",
            "value": "12/08/2020"
        },
        {
            "key": "date_issued",
            "value": "12/08/2020"
        },
        {
            "key": "coverage_paid",
            "value": "Business Recipient"
        },
        {
            "key": "bcc",
            "valueAsList": [
                "saranya@fiserv.com"
            ]
        },
        {
            "key": "cc",
            "valueAsList": [
                "madhan@gmail.com"
            ]
        }
    ]
}
```

### Sample Response (201 – Created)

```json
{
    "transactionId": "TID-807c3961-7c7b-483f-a7ca-555a05588e5b",
    "created": 1672659364,
    "merchantTransactionId": "merchantTransactionId-321540000011632",
    "recipient": [
        {
            "merchantCustomerId": "test8977",
            "recipientId": "8a7fbdcc8519d05e0185724438c01754",
            "payments": {
                "paymentId": "d7839999-a1c6-49a5-9478-a4985e4af89a",
                "paymentType": "Claims",
                "paymentStatus": "DP"
            },
            "portalUrl": "https://cat.digitalpayouts.com/?gid=EE680F#/authentication/guest/ZDc4Mzk5OTktYTFjNi00OWE1LTk0NzgtYTQ5ODVlNGFmODlhI1RJRC04MDdjMzk2MS03YzdiLTQ4M2YtYTdjYS01NTVhMDU1ODhlNWIrOGE3ZmJkY2M4NTE5ZDA1ZTAxODU3MjQ0MzhjMDE3NTQ="
        }
    ],
    "transactionStatus": "PD",
    "totalTransactionAmount": {
        "total": 35.00,
        "currency": "USD"
    }
}
```

## Sample Response (400 – Bad Request)
```json
{
    "code": "400024",
    "message": "Invalid request format/data.",
    "category": "common",
    "developerInfo": {
        "developerMessage": "Invalid request format/data.",
        "fieldError": [
            {
                "field": "paymentType",
                "message": "Payment Type not allowed."
            }
        ]
    }
}
```

[![Try it out](../../../../assets/images/button.png)](../api/?type=post&path=/ddp/v1/payments)
