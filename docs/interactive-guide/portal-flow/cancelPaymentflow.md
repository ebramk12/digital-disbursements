#Description

Merchant can only cancel payments that are in a “Pending” status. Once a disbursement method has been selected by the recipient, the payment is no longer able to be cancelled. After disbursement cancellation only applicable to ACH.

##Endpoint

<!-- theme: success -->
>**HTTP Method**: `PATCH`

>**Non-prod**: `https://int.api.firstdata.com/ddp/v1/payments/{merchantTransactionId}/cancel`

>**Prod**: `https://prod.api.firstdata.com/ddp/v1/payments/{merchantTransactionId}/cancel`


##Request Variables

| Name 					| 	Type 	| Maximum Length | Required  |
| --------------------- | -------	| ---------------| --------	 | 
| `merchantTransactionId` |  	String	| 32		 |	&#10004; | 

## Sample Request

```json
{
  "description": "Cancel transaction due to wrong amount."
}
```

### Sample Response (201 – Created)

```json
{
    "transactionId": "TID-14bcfec5-829b-4271-a0cb-9251272a7962",
    "transactionStatus": "TV"
}
```

## Sample Response (400 – Bad Request)
```json
{
    "code": "400029",
    "message": "Invalid request format/data.",
    "category": "common",
    "developerInfo": {
        "developerMessage": "Invalid request format/data.",
        "fieldError": [
            {
                "field": "transactionId",
                "message": "Invalid TransactionId."
            }
        ]
    }
}
```

[![Try it out](../../../../assets/images/button.png)](../api/?type=patch&path=/ddp/v1/payments/{id}/cancel)