##Description

Objective Merchant will want to initiate a payment for a Multi company recipient through the merchant portal and send email to recipient for the payment disbursement.

##Endpoint URL

HTTP Method: POST

Non-prod: [https://int.api.firstdata.com/ddp/v1/payments](https://int.api.firstdata.com/ddp/v1/payments)

Prod: [https://prod.api.firstdata.com/ddp/v1/payments](https://prod.api.firstdata.com/ddp/v1/payments)


##Parameters

| Name 					| Datatype 	| Parameter Type | Required | Max Length |
| --------------------- | -------	| -------------- | ---------| -----------|
| `Amount:currency` 	|  	String	|   	Body	 | yes 		| -			 |
| `Amount:total` 		|  	Number	|   	Body	 | yes 		| -			 |
| `merchantCustomerId` 	|  	String	|   	Body	 | yes 		| -			 |
| `recipientType` 		|  	String	|   	Body	 | yes 		| 32		 |
| `tin` 				|  	String	|   	Body	 | yes 		| -			 |
| `emailAddress` 		|  	String	|   	Body	 | yes 		| -			 |
| `phoneNumber`			|  	String	|   	Object	 | optional | -			 |
| `recipientIdentifier` |  	String	|   	Body	 | yes 		| Accepted values [Last_4_of_SSN, SPECIAL_CODE, ACCOUNT_NUMBER, DATE_OF_BIRTH, PHONE_NUMBER]			 |
| `recipientIdentifierValue` |  String	|   	Body	 | yes 	| -			 |
| `address` 			|  	String	|   	Body	 | yes 		| -			 |
| `payments` 			|  	String	|   	Body	 | yes 		| -			 |
| `merchantTransactionId` |  	String	|   	Body	 | yes 	| -			 |
| `batchNumber` 		|  	String	|   	Body	 | optional | -			 |
| `customFields` 		|  	String	|   	Body	 | optional | -			 |
| `doingBusinessAs` 	|  	String	|   	Body	 | yes 		| -			 |

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
        "total": 16,
        "currency": "USD"
    },
    "recipient": [
        {
            "recipientProfileInfo": {
                "recipientType": "Company",
                "merchantCustomerId": "merchantC2434234",
                "tin": "123456789",
                "emailAddress": {
                    "value": "gayathr3222222@fiserv.com",
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
                "doingBusinessAs": "Tech computers 1",
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
                "paymentType": "Claims"
            }
        },
        {
            "recipientProfileInfo": {
                "recipientType": "Company",
                "merchantCustomerId": "merc12233",
                "tin": "123456789",
                "emailAddress": {
                    "value": "gokul@fiserv.com",
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
                "doingBusinessAs": "Tech computers 2",
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
        "total": 16,
        "currency": "USD"
    },
    "recipient": [
        {
            "recipientProfileInfo": {
                "recipientType": "Company",
                "merchantCustomerId": "merchantC2434234",
                "tin": "123456789",
                "emailAddress": {
                    "value": "gayathr3222222@fiserv.com",
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
                "doingBusinessAs": "Tech computers 1",
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
                "paymentType": "Claims"
            }
        },
        {
            "recipientProfileInfo": {
                "recipientType": "Company",
                "merchantCustomerId": "merc12233",
                "tin": "123456789",
                "emailAddress": {
                    "value": "gokul@fiserv.com",
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
                "doingBusinessAs": "Tech computers 2",
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
                "paymentType": "Claims"
            }
        }
    ],
    "merchantTransactionId": "merchantTransactionId-102211",
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
            "key": "covrage_paid",
            "value": "Test"
        },
        {
            "key": "bcc",
            "valueAsList": [
                "saranya.gn1r@fiserv.com"
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
    "transactionId": "TID-957e6c64-a67d-4e61-aa20-5ace786c827c",
    "created": 1672659576,
    "merchantTransactionId": "merchantTransactionId-102211",
    "recipient": [
        {
            "merchantCustomerId": "merchantC2434234",
            "recipientId": "8a7fd5828519d047018572477400170b",
            "payments": {
                "paymentId": "6e0acb3e-32d2-48c5-a679-241ab326591c",
                "paymentType": "Claims",
                "paymentStatus": "DP"
            },
            "portalUrl": "https://cat.digitalpayouts.com/?gid=EE680F#/authentication/guest/NmUwYWNiM2UtMzJkMi00OGM1LWE2NzktMjQxYWIzMjY1OTFjI1RJRC05NTdlNmM2NC1hNjdkLTRlNjEtYWEyMC01YWNlNzg2YzgyN2MrOGE3ZmQ1ODI4NTE5ZDA0NzAxODU3MjQ3NzQwMDE3MGI="
        },
        {
            "merchantCustomerId": "merc12233",
            "recipientId": "8a7fbdcc8519d05e0185724776261758",
            "payments": {
                "paymentId": "e911574b-5b43-4534-a92c-9e7c171d264f",
                "paymentType": "Claims",
                "paymentStatus": "DP"
            },
            "portalUrl": "https://cat.digitalpayouts.com/?gid=EE680F#/authentication/guest/ZTkxMTU3NGItNWI0My00NTM0LWE5MmMtOWU3YzE3MWQyNjRmI1RJRC05NTdlNmM2NC1hNjdkLTRlNjEtYWEyMC01YWNlNzg2YzgyN2MrOGE3ZmJkY2M4NTE5ZDA1ZTAxODU3MjQ3NzYyNjE3NTg="
        }
    ],
    "transactionStatus": "PD",
    "totalTransactionAmount": {
        "total": 16.00,
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
