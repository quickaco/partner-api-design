## Create Business

Submits a new partner enabled business for KYC approval

### URL

  /partner/create-business

### Method

  `POST`

### Get URL Params

None

### Data Payload

```javascript
{
  "partner_reference": "$string",
  "user": {
    "first_name": "",
    "middle_name": "",
    "last_name": "",
    "address_line1" : "",
    "address_line2" : "",
    "suburb": "",
    "state": "",
    "postcode": "",
    "email_address": "",
    "phone_number": "+610000000",
    "date_of_birth": "1972-12-28",
    "branch_code": "123456",
    "account_number": "987654321",
    "id_document_type":"passport",
    "id_document_identifier": "",
    "id_pdf": "" // base64 encoded pdf
  },
  "business": {
    "business_name": "",
    "trading_name": "",
    "address_line1" : "",
    "address_line2" : "",
    "suburb": "",
    "state": "",
    "postcode": "",
    "industry_sector": "Health Care and Social Assistance",
    "trading_since": "1972-12-28",
    "website": "",
    "business_identifier":"58634810370",
    "branch_code": "123456",
    "account_number": "987654321"
  }
}
```

### Example snippit

```bash

curl --location --request POST 'https://my.quicka.co/v1/partner/check-business' \
--header 'Authorization: Bearer ${PARTNER_TOKEN}' \
--header 'Content-Type: application/json' \
--data-raw '{
    "partner_reference": "${PARTNER_REFERENCE}",
    "user": {
        "first_name": "allan",
        "middle_name": "scott",
        "last_name": "bond",
        "address_line1": "1 bond st",
        "address_line2": "lot 2",
        "suburb": "surry hills",
        "state": "new south wales",
        "postcode": "2000",
        "email_address": "m@m.com",
        "phone_number": "+61411111111",
        "date_of_birth": "2021-02-24T22:36:51.458Z",
        "branch_code": "062202",
        "account_number": "10011011",
        "id_docyment_type": "passport",
        "id_document_identifier": "123043493",
        "id_pdf": "aGVsbG8gd29ybGQ="
    },
    "business": {
        "business_name": "code-monkey",
        "trading_name": "special-man",
                "address_line1": "1 bond st",
        "address_line2": "lot 2",
        "suburb": "surry hills",
        "state": "new south wales",
        "postcode": "2000",
        "industry_sector": "health",
        "trading_since": "2021-02-24T22:36:51.458Z",
        "website": "",
        "business_identifier": "58634810370",
        "branch_code": "062202",
        "account_number":"10011011"
    }
}'

```

### Success Response

  * Code: 200 OK

```json
{
  "partner_reference" : "$string",
  "request_id" : "00000000-0000-0000-0000-000000000000",
  "status" : "queued"
}
```

### Error Response

You may trigger other 4XX/5XX error codes when supplying malformed data.

  * Code: 401 UNAUTHORIZED

```json
{
  "type": "Unauthorized",
  "message": "You are not authorised for this request.",
}
```



  * Code: 409 CONFLICT

```json
{
  "type": "Conflict",
  "message": "This partner reference was already used",
}
```



  * Code: 429 Too Many Requests

```json
{
  "type": "Too Many Requests",
  "message": "Too many requests. Please wait for 10 minutes and try again"
}
```



### Notes

This is an asynchronous request in so much as, the immediate reply will _not_ indicicate
succesful onboarding, only that the request is in our system. The reply will come in the form of a webhook response as follows:

Successful

```json
{
  "partner_reference": "$string",
  "business_id":"dc6bd866-1bd2-4011-9413-334dfb1f473e",
  "access_token":"8c3cf4d0-3b15-404f-bd85-6308a89220d1",
  "kyc_status":"success",
}
```

Successful partial

```json
{
  "partner_reference": "$string",
  "business_id":"dc6bd866-1bd2-4011-9413-334dfb1f473e",
  "access_token":"8c3cf4d0-3b15-404f-bd85-6308a89220d1",
  "kyc_status":"partial",
}
```

Failed Result

```json
{
  "partner_reference": "$string",
  "error": "Missing data: no match / no driver match etc",
  "kyc_status":"failed",
}
```
