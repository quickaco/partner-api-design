
## Check Business Onboarding Status

Requeues a request for onboarding information.
To be called when an update is required or hasn't been responded to.
The ${PARTNER_REFERENCE} is the value provided when calling create-business
previously.

### URL

  /partner/check-business/${PARTNER_REFERENCE}/

### Method

  `GET`

### Success Response

  * Code: 200


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


### Error Response

  *  Code: 404 NOT FOUND

     `{ "error" : "User doesn't exist" }`

  OR

  * Code: 401 UNAUTHORIZED
  
    `{ "error" : "You are not authorised for this request." }`


  * Code: 403 Forbidden
  
    `{ "error" : "You do not have permission to make this request." }`
