#Description

Objective Merchant will want to initiate a payment for a Multi consumer recipient through the merchant portal and send email to recipient for the payment disbursement.

##Endpoint

<!-- theme: success -->
>**HTTP Method**: `POST`

>**Non-prod**:  `https://int.api.firstdata.com/ddp/v1/payments`

>**Prod**: `https://prod.api.firstdata.com/ddp/v1/payments`


##Request Variables

| Name 					| 	Type 	| Maximum Length | Required  |
| --------------------- | -------	| ---------------| --------  | 
| `Amount:currency` 	|  	String	| 20			 |	&#10004; | 
| `Amount:total` 		|  	Number	| (16,4)		 |	&#10004; | 
| `merchantCustomerId` 	|  	String	| 100			 |	&#10004; | 
| `recipientType` 		|  	String	| 100			 |  &#10004; | 
| `firstName` 			|  	String	| 100			 |	&#10004; | 
| `lastName` 			|  	String	| 100			 |	&#10004; | 
| `emailAddress` 		|  	String	| 100			 |	&#10004; | 
| `phoneNumber`			|  	String	|  50			 |  		 |
| `recipientIdentifier` |  	String	| 100 (Accepted values [Last_4_of_SSN, SPECIAL_CODE, ACCOUNT_NUMBER, DATE_OF_BIRTH, PHONE_NUMBER]) | &#10004; | 
| `recipientIdentifierValue` |  String	| 100		 |	&#10004; |
| `address` 			|  	String	| -				 |	&#10004; | 
| `payments` 			|  	String	| -				 |	&#10004; | 
| `merchantTransactionId` |  String	| 100			 |	&#10004; | 
| `batchNumber` 		|  	String	| 100  		 	 | 		 	 |
| `customFields` 		|  	String	| -		   		 | 			 |

## Sample Request (Minimal information)

```json
{
    "amount": {
        "total": 10,
        "currency": "USD"
    },
    "recipient": [
        {
            "recipientProfileInfo": {
                "merchantCustomerId": "Madhan354233321",
                "recipientType": "Consumer",
                "firstName": "Madhan",
                "lastName": "kumar",
                "emailAddress": {
                    "value": "madhank@fiserv.com",
                    "type": "work",
                    "primary": true
                },
                "phoneNumber": {
                    "code": 1,
                    "value": "704-884-2754",
                    "type": "billing",
                    "extension": "2145"
                },
                "recipientIdentifier": "SPECIAL_CODE",
                "recipientIdentifierValue": "1234",
                "address": {
                    "type": "work",
                    "street": "1255 Corporate Drive",
                    "city": "Irving",
                    "stateOrProvince": "CA",
                    "postalCode": "91608",
                    "country": "USA",
                    "formatted": "1255 Corporate Drive,Irving, CA 91608 USA",
                    "primary": true
                }
            },
            "payments": {
                "paymentType": "Claims"
            }
        },
        {
            "recipientProfileInfo": {
                "merchantCustomerId": "vairamuthu2111",
                "recipientType": "Consumer",
                "firstName": "vairamuthu",
                "lastName": "chandrabalan",
                "emailAddress": {
                    "value": "vairamuthu.chand@fiserv.com",
                    "type": "work",
                    "primary": true
                },
                "phoneNumber": {
                    "code": 1,
                    "value": "704-884-1234",
                    "type": "billing",
                    "extension": "2145"
                },
                "recipientIdentifier": "SPECIAL_CODE",
                "recipientIdentifierValue": "7048842754",
                "address": {
                    "type": "work",
                    "street": "1255 Corporate Drive",
                    "city": "Irving",
                    "stateOrProvince": "CA",
                    "postalCode": "91608",
                    "country": "USA",
                    "formatted": "1255 Corporate Drive,Irving, CA 91608 USA",
                    "primary": true
                }
            },
            "payments": {
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
        "total": 10,
        "currency": "USD"
    },
    "recipient": [
        {
            "recipientProfileInfo": {
                "merchantCustomerId": "Madhan354233321",
                "recipientType": "Consumer",
                "firstName": "Madhan",
                "lastName": "kumar",
                "emailAddress": {
                    "value": "madhank@fiserv.com",
                    "type": "work",
                    "primary": true
                },
                "phoneNumber": {
                    "code": 1,
                    "value": "704-884-2754",
                    "type": "billing",
                    "extension": "2145"
                },
                "recipientIdentifier": "SPECIAL_CODE",
                "recipientIdentifierValue": "1234",
                "address": {
                    "type": "work",
                    "street": "1255 Corporate Drive",
                    "city": "Irving",
                    "stateOrProvince": "CA",
                    "postalCode": "91608",
                    "country": "USA",
                    "formatted": "1255 Corporate Drive,Irving, CA 91608 USA",
                    "primary": true
                }
            },
            "payments": {
                "paymentType": "Claims"
            }
        },
        {
            "recipientProfileInfo": {
                "merchantCustomerId": "vairamuthu2111",
                "recipientType": "Consumer",
                "firstName": "vairamuthu",
                "lastName": "chandrabalan",
                "emailAddress": {
                    "value": "vairamuthu.chand@fiserv.com",
                    "type": "work",
                    "primary": true
                },
                "phoneNumber": {
                    "code": 1,
                    "value": "704-884-1234",
                    "type": "billing",
                    "extension": "2145"
                },
                "recipientIdentifier": "SPECIAL_CODE",
                "recipientIdentifierValue": "7048842754",
                "address": {
                    "type": "work",
                    "street": "1255 Corporate Drive",
                    "city": "Irving",
                    "stateOrProvince": "CA",
                    "postalCode": "91608",
                    "country": "USA",
                    "formatted": "1255 Corporate Drive,Irving, CA 91608 USA",
                    "primary": true
                }
            },
            "payments": {
                "paymentType": "Claims"
            }
        }
    ],
    "merchantTransactionId": "merchantCustomerId-2220222-91",
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
    "transactionId": "TID-32a9356b-96b2-4a29-bdc8-c33bac94624f",
    "created": 1672658609,
    "recipient": [
        {
            "merchantCustomerId": "Madhan354233321",
            "recipientId": "8a7fd5828519d04701857238e0c81707",
            "payments": {
                "paymentId": "c62bf713-8001-4319-a05d-3ab10b5e7c02",
                "paymentType": "Claims",
                "paymentStatus": "DP"
            },
            "portalUrl": "https://cat.digitalpayouts.com/?gid=EE680F#/authentication/guest/YzYyYmY3MTMtODAwMS00MzE5LWEwNWQtM2FiMTBiNWU3YzAyI1RJRC0zMmE5MzU2Yi05NmIyLTRhMjktYmRjOC1jMzNiYWM5NDYyNGYrOGE3ZmQ1ODI4NTE5ZDA0NzAxODU3MjM4ZTBjODE3MDc="
        },
        {
            "merchantCustomerId": "vairamuthu2111",
            "recipientId": "8a7ff444749ce13601749d0a19ed0000",
            "payments": {
                "paymentId": "fa5c2fee-6559-4759-a610-fda1fe4f8d50",
                "paymentType": "Claims",
                "paymentStatus": "DP"
            },
            "portalUrl": "https://cat.digitalpayouts.com/?gid=EE680F#/authentication/guest/ZmE1YzJmZWUtNjU1OS00NzU5LWE2MTAtZmRhMWZlNGY4ZDUwI1RJRC0zMmE5MzU2Yi05NmIyLTRhMjktYmRjOC1jMzNiYWM5NDYyNGYrOGE3ZmY0NDQ3NDljZTEzNjAxNzQ5ZDBhMTllZDAwMDA="
        }
    ],
    "transactionStatus": "PD",
    "totalTransactionAmount": {
        "total": 10.00,
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