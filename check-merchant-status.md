
## Check Merchant Onboarding Status

Requeues a request for onboarding information.
To be called when an update is required or hasn't been responded to.
The ${PARTNER_REFERENCE} is the value provided when calling create-merchant
previously.

### URL

  /partner/check-merchant/${PARTNER_REFERENCE}/

### Method

  `GET`

### Success Response

  * Code: 200

    `{ id : 12, name : "Michael Bloom" }`

### Error Response

  *  Code: 404 NOT FOUND

     `{ "error" : "User doesn't exist" }`

  OR

  * Code: 401 UNAUTHORIZED
  
    `{ "error" : "You are unauthorized to make this request." }`
