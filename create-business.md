## Create Business

Submits a new partner enabled business for KYC approval

### URL

  /partner/create-business

### Method

  `POST`
  
### Get URL Params

None

### Data Payload

```json
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
    "id_pdf": ""
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

### Success Response

  * Code: 200 OK

    `{ "partner_reference" : "$string", "status" : "queued" }`

### Error Response

You may trigger other 4XX/5XX error codes when supplying malformed data.

  * Code: 401 UNAUTHORIZED
  
    `{ "error" : "You are not authorized to make this request." }`

  * Code: 409 CONFLICT
  
    `{ "error" : "This partner reference was already used" }`

  * Code: 429 Too Many Requests
  
    `{ "error" : "Too many requests. Please wait for 10 minutes and try again" }`

### Sample Call

  ```javascript
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
