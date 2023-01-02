##Description

Objective Merchant will want to initiate a payment for a single consumer recipient through the merchant portal and send email to recipient for the payment disbursement.

##Endpoint URL

HTTP Method: POST
Non-prod: [https://int.api.firstdata.com/ddp/v1/payments 
Prod: [https://prod.api.firstdata.com/ddp/v1/payments  

##Parameters

| Name 					| Datatype 	| Parameter Type | Required | Max Length |
| --------------------- | -------	| -------------- | ---------| -----------|
| `Amount:currency` 	|  	String	|   	Body	 | yes 		| -			 |
| `Amount:total` 		|  	Number	|   	Body	 | yes 		| -			 |
| `merchantCustomerId` 	|  	String	|   	Body	 | yes 		| -			 |
| `recipientType` 		|  	String	|   	Body	 | yes 		| 32		 |
| `firstName` 			|  	String	|   	Body	 | yes 		| -			 |
| `lastName` 			|  	String	|   	Body	 | yes 		| -			 |
| `emailAddress` 		|  	String	|   	Body	 | yes 		| -			 |
| `phoneNumber`			|  	String	|   	Object	 | optional | -			 |
| `recipientIdentifier` |  	String	|   	Body	 | yes 		| Accepted values [Last_4_of_SSN, SPECIAL_CODE, ACCOUNT_NUMBER, DATE_OF_BIRTH, PHONE_NUMBER]			 |
| `recipientIdentifierValue` |  String	|   	Body	 | yes 	| -			 |
| `address` 			|  	String	|   	Body	 | yes 		| -			 |
| `payments` 			|  	String	|   	Body	 | yes 		| -			 |
| `merchantTransactionId` |  	String	|   	Body	 | yes 	| -			 |
| `batchNumber` 		|  	String	|   	Body	 | optional | -			 |
| `customFields` 		|  	String	|   	Body	 | optional | -			 |

## Headers

Content-Type:application/json
Client-Request-Id:{{$guid}}
Api-Key:{{clientKey}}
Authorization:HMAC {{signature}}
Timestamp:{{time}}

## Sample Request (Minimal information)

```json
{
    "amount": {
        "total": 3,
        "currency": "USD"
    },
    "recipient": [
        {
            "recipientProfileInfo": {
                "address": {
                    "type": "work",
                    "street": "1255 Corporate Drive",
                    "city": "Irving",
                    "stateOrProvince": "CA",
                    "postalCode": "91608",
                    "country": "USA",
                    "formatted": "1255 Corporate Drive,Irving, CA 91608 USA",
                    "primary": true
                },
                "emailAddress": {
                    "value": "test1@gmail.com",
                    "type": "work",
                    "primary": true
                },
                "merchantCustomerId": "Test12344",
                "firstName": "Test",
                "lastName": "Kumar",
                "recipientType": "Consumer",
                "recipientIdentifier": "SPECIAL_CODE",
                "recipientIdentifierValue": "1234",
                "phoneNumber": {
                    "code": 1,
                    "value": "470-338-0000",
                    "type": "billing",
                    "extension": "2145"
                }
            },
            "payments": {
                "amount": {
                    "total": 3,
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
        "total": 3,
        "currency": "USD"
    },
    "recipient": [
        {
            "recipientProfileInfo": {
                "address": {
                    "type": "work",
                    "street": "1255 Corporate Drive",
                    "city": "Irving",
                    "stateOrProvince": "CA",
                    "postalCode": "91608",
                    "country": "USA",
                    "formatted": "1255 Corporate Drive,Irving, CA 91608 USA",
                    "primary": true
                },
                "emailAddress": {
                    "value": "test1@gmail.com",
                    "type": "work",
                    "primary": true
                },
                "merchantCustomerId": "madhan91722211222221",
                "firstName": "Test",
                "lastName": "Kumar",
                "recipientType": "Consumer",
                "recipientIdentifier": "SPECIAL_CODE",
                "recipientIdentifierValue": "1234",
                "phoneNumber": {
                    "code": 1,
                    "value": "704-884-0000",
                    "type": "billing",
                    "extension": "2145"
                }
            },
            "payments": {
                "amount": {
                    "total": 3,
                    "currency": "USD"
                },
                "paymentType": "Claims"
            }
        }
    ],
    "merchantTransactionId": "merchant2112222000090",
    "batchNumber": "454567",
     "customFields": [
        {
            "key": "claim_number",
            "value": "765033"
        },
        {
            "key": "payment_number",
            "value": "8745665"
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
            "value": "Test"
        },
        {
            "key": "bcc",
            "valueAsList": [
                "saranya.g@fiserv.com"
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
    "transactionId": "TID-09fd1699-34fc-4932-b269-4d4f671e5b1c",
    "created": 1672657661,
    "recipient": [
        {
            "merchantCustomerId": "madh3320000021",
            "recipientId": "8a7f769c82b795110182c3f94b6802d3",
            "payments": {
                "paymentId": "5e088d16-a08a-4e1c-bf1d-15dd036bbde1",
                "paymentType": "Claims",
                "paymentStatus": "DP"
            },
            "portalUrl": "https://cat.digitalpayouts.com/?gid=EE680F#/authentication/guest/NWUwODhkMTYtYTA4YS00ZTFjLWJmMWQtMTVkZDAzNmJiZGUxI1RJRC0wOWZkMTY5OS0zNGZjLTQ5MzItYjI2OS00ZDRmNjcxZTViMWMrOGE3Zjc2OWM4MmI3OTUxMTAxODJjM2Y5NGI2ODAyZDM="
        }
    ],
    "transactionStatus": "PD",
    "totalTransactionAmount": {
        "total": 3.00,
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
